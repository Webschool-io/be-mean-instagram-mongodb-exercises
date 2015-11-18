# Instanciação de variáveis no Javascript
Autor: **Mateus Cerezini Gomes**

Neste artigo vamos abordar alguns temas importantes sobre a instanciação de variáveis em JavaScript, entre eles: hoisting, closure, variáveis locais e globais, e IIFE.

## Hoisting
Em Javascript as variáveis são processadas antes de qualquer código na função, logo independe o local do *source code* ou função em que elas estão declaradas. Isso possibilita que variáveis sejam usadas antes de terem sido declaradas. Este comportamento é chamado de "hoisting", a variável é movida para o início da função ou do código global.

```
a = 2;
console.log(a); // 2
var a;

// é implicitamente entendido como:

var a;
a = 2;
console.log(a); // 2 
```

Por essa razão, recomenda-se sempre declarar variáveis na parte superior do seu escopo de aplicação (o topo do código global e a parte superior do código da função). Deixando claro na leitura do código que aquelas variáveis pertencem ao escopo local.

## Closure
Closures são funções que referenciam variáveis independentes (livres).  É um objeto especial que combina um função e as variáveis locais presentes no escopo no momento que é criado. Em outras palavras, a função definida no closure “lembra-se” do ambiente (valores das variáveis em um dado momento) em que foi criada.

```
function makeAdder(x) {
    return function(y) {
        return x + y;
    };
};

var add5 = makeAdder(5);
var add10 = makeAdder(10);

console.log(add5(2));  // 7
console.log(add10(2)); // 12
```

No exemplo podemos verificar que são criadas duas funções distintas, uma para *x=5* e outra para *x=10*. *add5* e *add10* são ambas closures. Elas compartilham o mesmo corpo de função mas guardam valores distintos para a variável *x*.

Closures são úteis para simular métodos e módulos privados, também podem ser usados sempre que for necessário um objeto com um único método.

```
var counter = (function() {
    var privateCounter = 0;
    function changeBy(val) {
        privateCounter += val;
    }
    return {
        increment: function() {
            changeBy(1);
        },
        decrement: function() {
            changeBy(-1);
        },
        value: function() {
            return privateCounter;
        }
    };
})();
```

No dado exemplo pode-se utilizar a variável *counter* para interagir com o contador, mas não se tem acesso a variável *privateCounter* ou ao método *changeBy*.

## Variável global
Variáveis globais são acessadas diretamente dentro do escopo da função desde que não tenham sido declaradas novamente ou seu identificador seja parêmetro da função, o que faria a variável global ser ignorada neste escopo. As alterações a variável global permanecem após a função finalizar.

```
var a = 10;
var b = function() {
    console.log(a);
}

var c = function() {
    var a = 3;
    console.log(a);
}

b(); //10
c(); //3
```

No exemplo a variável *a* é global, podendo ser acessada dentro de *b* e *c*, mas em c foi declarada um nova variável *a*, logo esta será local e nada será alterado na variável global.

## Variável por parâmetro
Na passagem de parâmetros para uma função é criado um objeto *argumentos* semelhante a um array com os parâmetros passados, é feita uma cópia dos valores e/ou referências no caso de objetos. Logo as modificações nestes parâmetros estarão limitadas ao escopo dessa função, com excessão para os parâmetros de objetos referenciados.

Variáveis globais se passadas como argumentos da função vão se comportar como variáveis locais onde as alterações locais só persistem no escopo da função.

```
var a = 10;
var b = function(x) {
    x = 30; 
    console.log(x,a);
}

b(a); // 30 10
```
 
## IIFE
Immediately-invoked function expressions (IIFE) são usadas para evitar hoisting das variáveis dentro de um bloco de código, evitando a poluição do ambiente global de variáveis e simultaneamente permitindo acesso público à métodos enquanto mantém a privacidade de variáveis definidas dentro da função.

Os IIFEs são declarados dentro de parênteses com a passagem direta dos parâmetros, para um variável receber um valor basta que a função IIFE contenha um *return*. O simples exemplo à seguir demonstra esta situação:

```
var resultadoSoma = (function(a, b) {
    return a + b;
})(10, 100);

console.log(resultadoSoma); // 110 
```

Também são usados para criar variáveis e métodos privados:

```
var counter = (function(){
    var i = 0;

    return {
        get: function(){
            return i;
        },
        set: function( val ){
            i = val;
        },
        increment: function() {
            return ++i;
        }
    };
})();
```

## Conclusão
Entender que a linguagem JavaScript usa o escopo de função em vez do escopo de bloco na instanciação de variáveis é fundamental para entender o seu funcionamento e programar de maneira eficiente e correta. 

## Referências bibliográficas

* [MDN Variáveis](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/var)
* [MDN Closure](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Closures)
* [IIFE](https://nandovieira.com.br/design-patterns-no-javascript-singleton)
* [IIFE Wikipedia](https://en.wikipedia.org/wiki/Immediately-invoked_function_expression)
