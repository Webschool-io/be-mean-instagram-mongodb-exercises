# Artigo
**autor**: Dayvson Sales

**Prazo**: até dia 18 de Novembro de 2015

Neste artigo irei abordar resumidamente os tópicos Hoisting, Closure, Variável Global, por parâmetro e IIFE.

## Hoisting

Hoisting é um comportamento do JavaScript que consiste em enviar todas as declarações de variáveis ao topo do escopo antes de processá-las. Sendo assim, é possível atribuir um valor a uma variável antes de cria-la.

```
numero = 10;
console.log(numero);
var numero;

```

Em nosso código escrito, ```numero``` está sendo utilizado antes mesmo de ser declarado e o código acima funciona. O código abaixo demonstra como ele fica após o JavaScript interpretá-lo e mandar todas as variáveis para o topo do escopo.

```
var numero;
numero = 10;
console.log(numero);
```

O hoisting funciona apenas para a declaração de variáveis e não para a inicialização delas.

```
var a = 8;

console.log(a); //8
console.log(b); //undefined

var b = 7;

```

No exemplo acima, o valor de b não é 7 pois apenas as *declarações* vão para o topo do escopo. Esse exemplo é o mesmo que:

```
var a = 8;
var b;
console.log(a); //8
console.log(b); //undefined
b = 7;
```

Por esse comportamento, é uma boa prática declarar sempre as variáveis no topo de cada escopo. 

Obs.: caso o ‘use strict’ esteja ativado, declarar a variáveis após usá-las não irá funcionar.

## Closure

(eu não sei muito sobre closure, então minha explicação está bem newbie. por conta do prazo ser até hoje, vou colocar bem superficial. talvez com o tempo melhore meus conhecimentos e atualize essa parte)

Segundo Wikipédia, "Closure are a technique for implementing lexically scoped name binding in languages with first-class functions.". 
O código abaixo mostra um exemplo de Closure em JavaScript.

```
function mensagemPersonalizada(nome){
  
  var mensagem = "Olá";

  return function(){
        console.log(mensagem + nome);
  }

}

var cumprimento = mensagemPersonalizada("Voce");
cumprimento(); //Olá Voce

```

Analisando passo-a-passo o que acontece nesse código temos:

1 - Criamos uma função chamada mensagemPersonalizada  
2 - Essa função retorna uma outra função anônima  
3 - Dentro dessa função há uma inicialização de variável chamada mensagem  
4 - Guardamos o retorno da chamada dessa função na variável cumprimento  
5 - Fim da execução da mensagemPersonalizada, é chamado o Garbage Collector para limpar o que não mais será utilizado  

Assim, no final de tudo o que guardamos na variável ``cumprimento`` é apenas a função anônima retornada.
Como no código abaixo:

```
var cumprimento = function(){ console.log(mensagem + nome); }
cumprimento(); //undefined
```

Se executassemos somente esse código, um erro seria lançado, pois ``mensagem`` e ``nome`` não existem nesse escopo. 
Mas quando o JavaScript encontra um closure, o Garbage Collector não é acionado, fazendo com que as *referências* ainda estejam disponíveis na função retornada e que possam ser utilizadas. Esse é o segredo do closure.

## Variável Global

Como em muitas linguagens, JavaScript possui a característica de permitir variáveis globais, que podem ser acessadas de qualquer lugar.
Para definir uma variável global basta declará-la fora de qualquer escopo de função. 

```
var numero = 20; //global

function t(){
  var a = 10; //local
  console.log(numero); //20
}

console.log(numero); //20
console.log(a); // undefined
t();
```

É possível alterar os valores de uma variável global, mas é preciso ter em mente que alterando em um local, irá alterar em todos os outros que a utilizam.


## Variável por parâmetro

Em JavaScript podemos passar para uma função valores que iremos utilizar na função, essas variáveis estarão disponiveis para serem utilizadas na função.  

Exemplo:

```
function soma(a, b){
   console.log(a + b);
}
```
Caso os nomes das variáveis na função sejam idênticos à variáveis globais, será utilizado os de escopo local. 

Uma característica interessante também é que é possível chamar uma função que possui parâmetros sem passá-los ou chamar uma função que não possui parâmetros passando parâmetros. Nesse último caso, é possível acessar as variáveis através do ``arguments``, isso chama-se passagem de múltiplos parâmetros (na ES6 há um operador próprio para isso). 

 ```
 //utilizando a função soma anterior
 soma(); //NaN
 
 function somaMultipla(){
    var args = [].slice.call(arguments);
    var i;
    var soma = 0;
    for(i = 0; i < args.length; i++){
        soma += args[i];
    }
    console.log(soma);
 }
  
 somaMultipla(1, 2, 3, 4, 5, 6); //21
 somaMultipla(2,3,4); //9

 ```

Outro ponto importante a ser citado é que é possível ser passado funções por parâmetros. Isso é bastante utilizado como forma de callback, importante por conta da característica assíncrona do JavaScript.

```
function chamada(cumprimento, nome){
   cumprimento(nome);
}

chamada(function(nome){ console.log("Olá, " + nome);}, "cara");

```

## Instanciação usando uma IIFE

IIFE significa Immediately-Invoked Function Expression, este tipo de função é executado no mesmo momento que é definida.

```

(function(){
    var a  = 10;
    console.log(a);
}())

```

É muito utilizada para isolar variáveis do escopo global, quando definimos uma variável nesta função, não podemos acessá-la fora dela.

```

(function(){
    var a  = 10;
    console.log(a);
}())

console.log(a); //Reference Error

```

Também é possível passar parâmetros para uma IIFE.

```
(function(a){ console.log(a); }("ola"))

```

Uma IIFE pode retornar uma função, que poderá ser atribuida a uma variável e utilizada.

```
var soma = (function(){ return function(a, b){ console.log(a+b); }}())
soma(1, 2);

```
