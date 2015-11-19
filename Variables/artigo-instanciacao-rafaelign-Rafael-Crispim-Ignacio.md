# Instâncias em Javascript
**autor**: Rafael Crispim Ignácio

## Hoisting
Este termo foi cunhado por **Ben Cherry** e é usado para explicar o comportamento do javascript definir a prioridade das declarações e inicializações de variáveis e funções.

### Variable Hoisting
As varíaveis tem a sua declaração elevada para o topo do escopo(hoisted), mas não a sua inicialização.

```
try {
    console.log(foo);
} catch (e) {
    console.error('variável `foo` não definida.');
}
// Cai no catch

try {
    console.log(foo)
    var foo = 2
} catch (e) {
    console.error('A variável `foo` não foi definida.')
}
// Não cai no catch, mas imprime `undefined`
```

### Function Hoisting
As funções têm a sua declaração e o seu corpo elevados ao topo(hoisted).

```
function foo(){
    function bar() {
        return `foo`
    }

    return bar()

    function bar() {
        return `bar`
    }
}

console.log(foo())
// Imprime `bar`
// Neste caso, devido ao efeito do hoisting, a segunda declaração de bar()
// sobreescreve a primeira e o resultado impresso é `bar`
```

## Closure
São funções que mantém o ambiente em que foram criadas, ou seja, ela consegue referenciar a variáveis que foram declaradas fora do escopo global.

Para utlizar closures, basta criar uma função e retornar uma outra função que manipula variáveis declaradas no escopo global ou no escopo da função pai.

```
function makeFoo() {
  var a = "FooBar";
  function foo() {
    alert(a);
  }
  return foo;
}

var bar = makeFoo();
bar();
```

Em geral, este recurso pode ser utilizado na manipulação de eventos acionados por usuários, funcionando como uma função de callback.

## Variável Global
Todas as variáveis declaradas dentro das tags `<script>` que estejam fora de funções são globais. Estas variáveis são acessíveis em todos escopos. Para acessar uma variável global dentro de uma função, basta fazer o acesso diretamente a variável como se ela já existisse no ecopo atual.

```
var bar = 0;
function foo(){
    console.log(bar);
    // -> 0
    bar = 1;
}
foo();
console.log(bar);
// -> 1
```

## Variável por parâmetro
Quando passamos um parâmetro em uma função, este se torna uma variável local para o escopo daquela função. É como se fizessemos uma declaração de uma variável dentro do escopo daquela função.

```
function foo(bar) {
    console.log(bar)
}
foo("foobar");
// -> `foobar`

console.log(bar);
// -> bar is not defined
```

O mesmo ocorre para as variáveis globais. Quando estas são passadas como parâmetro é como se fizessemos uma cópia de seu conteúdo para uma variável com o mesmo nome mas de escopo local. Qualquer alteração feita nesta variável permanecerá no escopo local, não sendo replicado para o escopo global.

```
var a = 'foobar';
function foo(bar) {
    bar = 'barfoo'
    console.log(bar)
}
foo(a);
// -> `barfoo`

console.log(a);
// -> `foobar`
```

## Instanciação usando uma IIFE
IIFE significa "Immediately-invoked function expression" e ela é utilizada para encapsularmos o escopo no javascript de uma forma que as declarações globais não venham a interfirir no que está dentro dela. Sua execução é feita na declaração.

```
(function(){ ... })();
```

Desta forma, uma variável só pode receber um valor utilizando o return dentro da função imediata, onde conseguimos exportar algum resultado que foi processado.

Quando passamos um parametro em uma IIFE, o estado global deste parametro será mantido mesmo que este sofra alteração dentro da função imediata, diferentemente do que ocorre quando manipulamos dentro de um método comum. Para passar um parâmetro para uma IIFE basta adicioná-lo na declaração e adicionar o valor desejado na chamada que segue a declaração.

```
(function(x, y){
    console.log(y, x);
    // -> `bar foo`
})(`foo`, `bar`);
```

## Referências
[http://tecnologia-simples.blogspot.com.br/2012/04/variaveis-globais-e-locais-javascript.html](http://tecnologia-simples.blogspot.com.br/2012/04/variaveis-globais-e-locais-javascript.html) [https://www.turbosite.com.br/blog/entenda-o-que-sao-closures-em-javascript](https://www.turbosite.com.br/blog/entenda-o-que-sao-closures-em-javascript) [https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Guide/Closures](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Guide/Closures) [http://nodebr.com/cuidado-com-a-armadilha-do-escopo-de-variaveis-em-javascript/](http://nodebr.com/cuidado-com-a-armadilha-do-escopo-de-variaveis-em-javascript/) [http://imasters.com.br/front-end/javascript/sobre-funcoes-imediatas-javascript-iife/](http://imasters.com.br/front-end/javascript/sobre-funcoes-imediatas-javascript-iife/) [http://loopinfinito.com.br/2014/10/29/hoisting-e-escopo-em-javascript/](http://loopinfinito.com.br/2014/10/29/hoisting-e-escopo-em-javascript/)
