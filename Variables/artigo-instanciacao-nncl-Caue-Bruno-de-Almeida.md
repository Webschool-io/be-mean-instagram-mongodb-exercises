# JS - Instanciação
**autor**: Cauê Bruno de Almeida

Neste artigo veremos algumas premissas do JS quanto suas funcionalidades.

## Hoisting

No JS, você pode utilizar uma variável **antes mesmo** de criá-la. Ex:

```
pokemon = 'Pikachu';
document.querySelector('p').innerHTML = pokemon;

var pokemon;
```

Ou com uma função:

```
myFunc();

myFunc = function() {
  alert('Hello!');
}
```

### Como isso aconteceu?

Hoisting é um comportamento que move automaticamente todas as declarações para o início do escopo. Ou seja, quando o browser começa a ler o código, a declaração da variável/função já está no início do escopo.

Para evitarmos futuros problemas, `use strict`.

## Closure

Veja o exemplo:

```
for(var i = 0; i <= 3; i++) {
  document.getElementById('btn').onclick = function() {
    console.log(i);
  }
}
```

Você pode achar que o código acima vai mostrar o que a ideia original deve mostrar, mas incrivelmente - ou não - vai mostrar sempre 4.

Por que isso acontece? Porque funções têm acesso ao escopo externo de onde foi criada, e no `for` a variável `i` já tem o valor 4.

Agora se eu alterasse o `id` do botão para:
```
...
document.getElementById('btn' + i)
...
```

Por que funciona? Simples: porque o código está sendo executado no momento, que está sem closure. Ou seja, ele pega o valor atual do `i` ao decorrer do loop.

**Dica**: você pode usar uma closure se precisar declarar uma função privada. As closures as emularia.

Exemplo:

```
var myVar = (function() {
  hello = function() {
    console.log( 'Hello' );
  }

  return {
    sayHello : function() {
      hello();
    }
  };
})()
```

Aqui a função `sayHello` só pode ser usada dentro do escopo de `myVar`.


## Variável Global

Uma variável global é uma variável declarada fora de uma função. Sendo assim, você pode usá-la em qualquer função/objeto/etc. Ex:

```
var age = 19;

showAge = function() {
  alert( age );
}
```

## Variável por parâmetro

Explique o que acontece dentro da função qnd um parâmetro é passado e também explique quando uma GLOBAL é passada por parâmetro.

Vamos supor que fizéssemos assim:

```
var age = 19;

showAge = function(age) {
  alert( age );
}
```

Isso na verdade não é preciso, pois `age` já pode ser utilizado sem ter de passarmos como parâmetro justamente pela função ter acesso ao escopo externo do exemplo.
Agora, e se passásemos a variável `age` com o valor igual a 20, dentro da função? Quem a função mostraria?

```
var age = 19;

showAge = function() {
  var age = 20;
  alert( age );
}

showAge();
```

Nesse caso, mostraria 20 porque ela pega a última variável declarada, mas percebe que isso pode se tornar um problema futuramente em um outro caso?

## Instanciação usando uma IIFE

Uma IIFE é uma função executada na mesma hora em que é definida. Ex:

```
(function(){
  'use strict'

  var hello = 'world';
  console.log(hello);
})
```

Agora como podemos receber um valor de uma IIFE. Vamos supor que em uma página que eu chamo a seguinte função:

```
;(function( window, document, $, undefined ) {
  'use strict';

  var app = (function(){
    hello = function(name) {
      alert('Hello ' + name);
    }
  })();

  window.app = app;
  app.hello();

})( window, document, jQuery );
```

Agora em outra página, que não chama o arquivo que contém o JS acima, eu preciso usar a mesma função `hello(name)`. Como? Assim:

```
var name = 'Clyde';
var diffHello = window.app.hello( name );
```
