# Variáveis e Funções no JavaScript: criação e instanciação
**Autor**: [Alexandre R. Janini](https://github.com/ajanini)

A declaração de variáveis no JavaScript pode ser confusa até para programadores experientes. É fácil esquecer de declarar uma variável com o operador `var` precedendo seu nome, o que pode gerar problemas de escopo no código. Problemas similares podem ocorrer com funções.

## Escopo

Apesar de ser da família das linguagens baseadas em C, o escopo de variáveis no JS é diferente dessas linguagens. O escopo do JavaScript não se dá por blocos, mas sim por funções. Na prática, isso significa que uma variável redeclarada dentro de um bloco `if` (por exemplo) no JS, altera o valor da mesma fora do bloco `if`, diferente do C. Veja o exemplo a seguir.

```javascript
var a = 1;
console.log(a);

if (true) {
    var a = 2;
    console.log(a);
}

console.log(a);
```

O código acima irá imprimir no console:
```
1
2
2
```

Como pode-se verificar, ao se trocar o valor da variável `a` para `2` dentro do bloco `if`, o valor original da variável é alterado.

Este comportamento é diferente de um código equivalente em C, no qual o valor da variável fora do `if` continuaria com o valor de `1`.

Como já foi mencionado, no JS o escopo de variáveis se dá por funções. Para se obter o mesmo comportamento do código equivalente em C, devemos usar uma IIFE (*Immediately-Invoked Function Expression*, ou Expressão de Função Invocada Imediatamente), como no exemplo abaixo:

```javascript
var a = 1;
console.log(a);

if (true) {
    // Abaixo começa a IIFE
    (function() {
        var a = 2;
        console.log(a);
    }());
    // Fim da IIFE
}

console.log(a);
```

O código acima irá produzir o resultado equivalente ao mesmo código em C:

```
1
2
1
```

Isso ocorre porque no JS o escopo das variáveis se dá por funções e não por blocos, e a IIFE é justamente isso: uma função.

## Hoisting

O termo *hoisting* foi cunhado por [Ben Cherry](http://twitter.com/bcherry) e define o comportamento da resolução de nomes e inicialização de valores das variáveis e funções no JavaScript.

*Hoist* em inglês significa levantar/suspender com auxílio de um aparato mecânico. Quando declaramos uma variável no JS, ela é "elevada" para o topo do escopo.

### Hoisting de variáveis

Sempre que uma variável é definida no JS, sua declaração é elevada ao topo do escopo, mas seu valor não é inicializado. Os códigos abaixo exemplificam isso.

```javascript
try {
    console.log(a);
} catch (e) {
    console.error('A variável "a" não foi definida.');
}
```

Resulta em `A variável "a" não foi definida.` impresso no console.

Claro, já que a variável não foi declarada, o bloco `try/catch` captura o erro e exibe a mensagem.

Diferente do exemplo a seguir:

```javascript
try {
    console.log(a);
    var a = 2;
} catch (e) {
    console.error('A variável `a` não foi definida.');
}
```

Que resulta em `undefined` impresso no console.

Veja que apesar da variável `a` ter sido declarada **depois** do comando `console.log()`, a declaração foi elevada no escopo. Assim, uma exceção não é disparada e o bloco `try/catch` não cai no `catch`. **Porém**, o valor da variável não está definido durante o *hoisting* (a variável não é inicializada), imprimindo assim o `undefined` no console.

Na prática, portanto, o código poderia ser escrito como abaixo, para que fique mais fácil para nós, humanos, entendermos como o JavaScript trabalha com as variáveis implicitamente:

```javascript
try {
    var a;
    console.log(a);
    a = 2;
} catch (e) {
    console.error('A variável `a` não foi definida.');
}
```

### Hoisting de funções

A declaração e inicialização de funções ocorre de maneira diferente. Tanto a declaração como a inicialização das funções são elevadas (*hoisted*). Veja o exemplo:

```javascript
foo();
function foo() {
    console.log('bar');
}
```

O resultado é `bar` impresso no console. Note que mesmo chamando-se uma função que ainda não foi declarada, não ocorre nenhum erro e a função executa como esperado. Novamente, isso ocorre porque a função toda é elevada.

Um exemplo mais complexo segue:

```javascript
function foo() {
    function bar() {
        return 3;
    }

    return bar();

    function bar() {
        return 8;
    }
}
```

Se pensarmos de maneira linear, esperaríamos que o resultado no console seria `3`. No entanto, devido ao *hoisting*, o resultado obtido é `8`. Isso porque a função `bar` abaixo do `return` é elevada, e sobrescreve a função de mesmo nome, retornando portanto `8`.

***

Há uma outra forma de definir funções no JS: como uma expressão. Neste caso, elas serão tratadas como variáveis, sendo apenas seus nomes elevados, mas não sua inicialização.

```javascript
foo();
var foo = function() { console.log('bar') };
```

O código acima resultará num `TypeError: foo is not a function`. A variável `foo` está declarada, mas é `undefined` e, portanto, não é uma função.

## Closures

De maneira simples, uma *closure* é "uma função interior que tem acesso a variáveis de uma função exterior". *Closures* são poderosas porque tem acesso à três cadeias de escopo:

* Escopo próprio (variáveis definidas dentro de suas chaves);
* Variáveis da função exterior (e seus parâmetros);
* Variáveis globais.

Basicamente, uma *closure* é uma função dentro de outra função. Como no exemplo a seguir:

```javascript
function showName (firstName, lastName) {
    var nameIntro = "Seu nome é ";

    // Esta função interior tem acesso as variáveis da função exterior, incluindo os parâmetros
    function makeFullName () {
        return nameIntro + firstName + " " + lastName;
    }

    return makeFullName ();
}

showName ("Michael", "Jackson");
```

O retorno da função será `Seu nome é Michael Jackson`.

*Closures* são muito usadas no jQuery e no Node.js. Elas emulam propriedades e métodos privados.

Algumas propriedades e efeitos colaterais importantes de *closures*:
1. *Closures* tem acesso à variável das funções exteriores **mesmo após o retorno** da função exterior;
2. *Closures* armazenam **referências** para as variáveis da função exterior, e não seus valores em si;
3. A propriedade 2, acima, pode gerar efeitos colaterais. Pode ser necessário usar IIFEs (veja no tópico específico, abaixo, sobre isso) para usar valores previamente declarados e não suas referências.

## Variáveis globais

Considerando-se o escopo do JavaScript já discutido anteriormente, uma variável "global" pode ser definida apenas declarando-a fora de qualquer função. No exemplo abaixo, a variável `foo` pode ser considerada como uma variável global:

```javascript
var foo = 'bar'; // variável global
function xitzabutz ()
{
    console.log('Eu adoro ir no ' + foo + '!');
}
xitzabutz();
```

O código acima resultará em `Eu adoro ir no bar!` impresso no console.

Qualquer alteração à variáveis globais dentro de funções resultará na alteração da variável para todo o escopo. Portanto, se continuarmos considerando o código acima e acrescentarmos:

```javascript
function cacilds()
{
    foo = 'supermercado';
}
cacilds();
xitzabutz();
```

Resultará em `Eu adoro ir no supermercado!` impresso no console.

## Variáveis por parâmetro

Uma variável pode ser passada para uma função como um parâmetro:

```javascript
var foo = 'bar';
function gorlomi (where)
{
    console.log('Meu lugar favorito para ir no fim da tarde é em um ' + where + '!');
}
gorlomi(foo);
```

Resultará em `Meu lugar favorito para ir no fim da tarde é em um bar!` no console.

Ao se passar uma variável global como um parâmetro, ao se alterar o parâmetro dentro da função, o valor da variável global permanece inalterado:

```javascript
var foo = 'bar';
function margheriti (where)
{
    where += ', ou não';
    console.log('Meu lugar favorito para ir logo cedo é em um ' + where + '!');
}
margheriti(foo);
console.log('O valor de "foo" não foi alterado: ', foo);
```

Resulta em:

```
Meu lugar favorito para ir logo cedo é em um bar, ou não!
O valor de "foo" não foi alterado:  bar
```

## Instanciação usando uma IIFE

Vamos nos aprofundar um pouco no tópico das IIFEs.

Uma IIFE é um *design pattern* do JavaScript que produz um escopo estático, fazendo uso do escopo por funções do JavaScript de maneira a isolar partes do código de alterações em variáveis que podem ser indesejadas. Assim, elas podem ser usadas para evitar a "poluição" de escopo ao evitar o *hoisting* de certas variáveis.

Exemplo de uma IIFE:

```javascript
var foo = 'bar';
(function() {
    var foo = 'boteco';
    console.log('Vamos pro ' + foo + '!');
})();
console.log('Valor de "foo" é:', foo);
```

Além de ser executada imediatamente, a IIFE mantém o valor da variável global `foo` inalterado, apesar de redefini-la dentro de seu escopo estático, resultando no seguinte impresso no console:

```
Vamos pro boteco!
Valor de "foo" é: bar
```

Uma variável pode receber o valor da uma IIFE quando a IIFE retorna um valor:

```javascript
var foo = 'bar';
var vamos = (function(){ return 'Vamos ao ' + foo; })();
console.log(vamos);
```

Resulta na impressão de `Vamos ao bar` no console.

O seguinte exemplo mostra como passar parâmetros para uma IIFE e o que acontece com eles dentro da função e fora dela.

```javascript
var onde = 'bar';
var bebida = 'cerveja';
var resultado = (function(a, b) {
    b += ' e comer pastéis';
    var frase = 'Hoje nós vamos no ' + a + ' beber ' + b + '.';
    return frase;
})(onde, bebida);
console.log(resultado);
console.log(bebida);
console.log(a);
console.log(b);
```

Resultará em:

```
Hoje nós vamos no bar beber cerveja e comer pastéis.
cerveja
ReferenceError: a is not defined
ReferenceError: b is not defined
```

Portanto, alteramos o valor do parâmetro dentro da IIFE, sem alterar o valor original da variável global usada como parâmetro.
Da mesma forma, os valores de `a` e `b`, não existem fora do escopo da IIFE.

## Bibliografia

* [Hoisting e escopo em JavaScript no Loop Infinito](http://loopinfinito.com.br/2014/10/29/hoisting-e-escopo-em-javascript/) por Caio Gondim - Acesso em 17 de novembro de 2015;
* [Entenda Closures no JavaScript com Facilidade no Javascript Brasil](http://javascriptbrasil.com/2013/10/12/entenda-closures-no-javascript-com-facilidade/) por Eric Oliveira - Acesso em 17 de novembro de 2015;
* [How do JavaScript closures work? no Stack Overflow](http://stackoverflow.com/questions/111102/how-do-javascript-closures-work) - Acesso em 17 de novembro de 2015;
* [Javascript global variables no Stack Overflow](http://stackoverflow.com/questions/4862193/javascript-global-variables) - Acesso em 17 de novembro de 2015;
* [Immediately-invoked function expression na Wikipedia](https://en.wikipedia.org/wiki/Immediately-invoked_function_expression) - Acesso em 17 de novembro de 2015;