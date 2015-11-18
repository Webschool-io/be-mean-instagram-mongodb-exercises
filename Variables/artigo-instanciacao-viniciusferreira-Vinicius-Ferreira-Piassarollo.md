# Artigo - Instanciação no Javascript
 
**autor**: VINICIUS FERREIRA PIASSAROLLO


Explique, com teoria e código, nesse artigo como o JavaScript cria e instancia as variáveis, seguindo os seguintes tópicos.


## Hoisting


Explique o que é, o porquê acontece e como acontece com variável e função.



```

Hoisting (tradução seria levantar) a forma que o JavaScript trata a declaração das variáveis; onde independente da linha onde foram declaradas ( se mais no topo, ou mais abaixo) O Hoisting faz as variáveis ser "levadas" para o topo do código;

Exatamente se tu escrever a variavel no topo ou abaixo do código o Hoisting faz que isso se torne irrelevante; ou seja, em JavaScript quando declaramos uma variável ou função ela sobe para o topo do escopo. O Hoisting leva para o topo somente a declaração desta variável e não leva sua intanciação junto;

No Js existem dois tipos de Hoisting:  Variable hoisting e a Function hoisting.  Variable hoisting seria a possibilidade de se declarar uma variável  em qualquer parte do seu código, Ja o Function hoisting sendo equivalente a declarar no início da função ou do código global.

Isso ocorre no Javascript porque as variáveis e as funções são processadas antes que o código seja executado, possibilitando declarar uma variável ou função em todas partes do código. Todavia é mais interessante declarar no início para manter uma estética e facilitar o desenvolvimento;

  function xx () {
    console.log(zz);
  }
  xx();

  O código acima da um erro, porque a var zz não existe.

  function xx () {
    console.log(zz);
    var zz = 999;
    console.log(zz);
  }
  xx(); 

  Já agora vai printa  undefined e 999; show o Hoising;

```



## Closure


Explique o que é, o porquê acontece e como usar. 
Cite situações que você usaria.



```
Em JavaScript, as closures são  funções para a qual as variáveis ​​do contexto circundantes estão vinculados por referência.

Um Closure é uma função interna que tem acesso a cadeia de variáveis ​​escopo da função exterior ( envolvente ) . O fechamento tem três cadeias de escopo : ele tem acesso ao seu próprio âmbito de aplicação ( variáveis ​​definidas entre as suas chaves ) , ele tem acesso a variáveis ​​da função exterior , e tem acesso às variáveis ​​globais.

A função interna tem acesso não apenas às variáveis ​​da função externa , mas também para os parâmetros da função externa . Note que a função interna não pode chamar argumentos da função objeto exterior , no entanto, mesmo que ele pode chamar os parâmetros da função externa diretamente.

Resumo closure é uma função interna, que te permite acessar variáveis externas; Onde se cria um Closure , adicionando uma função dentro de outra função;

Entendendo sobre o escopo das variáveis, ou seja o ambiente onde você declarou sua variável, esse ambiente demarca o limite onde você pode usar sua variável.

Abaixo cito um exemplo de função  dentro de outra função, onde a função que está dentro, tem acessos a dados da função que está fora, isso é uma function closure.

Cite situações que você usaria.? 

Uma função pode acessar todas variáveis criadas dentro dela, e com as closures podemos acessar também variáveis criadas do lado de fora, sem bagunçar nosso escopo global deixando o codigo mais organizado.

EXEMPLO TIO:

function getMeAClosure() {
    var canYouSeeMe = "here I am";
    return (function theClosure() {
        return {canYouSeeIt: canYouSeeMe ? "yes!": "no"}; 
    });
}
 
var closure = getMeAClosure();
closure().canYouSeeIt; //"yes!"

```



## Variável Global

Explique como se usa uma var Global dentro de uma função.


```

Variável Global são variáveis  acessíveis em todos escopos, Ou seja, as  variáveis declaradas fora de funções tem escopo global. Para lhes acessar dentro de uma função, basta fazer o acesso direto a variável como se se a variável existisse dentro desta função.

var bar = 0;
function foo(){
    console.log(bar);
    //////  bar = 0;
    bar = 5;
}
foo();
console.log(bar);
     /////  bar = 5;


```







## Variável por parâmetro

Explique o que acontece dentro da função qnd um parâmetro é passado e também explique quando uma GLOBAL é passada por parâmetro.

```

qnd se passa um parâmetro para uma function, este se torna uma variável local para essa function. É como se declarasse de uma variável dentro do escopo da função.

function foo(bar) {
    console.log(bar)
}
foo("foobar");
////// printa    `foobar`

console.log(bar);
////// printa    bar is not defined


Explique quando uma GLOBAL é passada por parâmetro.-->

Simples tio é como se fizessemos uma cópia de seu valor para uma outra variável escopo local. Qualquer alteração feita fica nesse escopo da função, e a variavel global tem seu valor inalterado tipo magia negra pra alguns hihiihihihhi loco neh tio ?


```

## Instanciação usando uma IIFE

Explique como uma variável pode receber um valor de uma IIFE.

Explique como passar uma variável por parâmetro para a IIFE e acontece com ela dentro da função.

```
Em Javascript funções podem ser declaradas tanto através de uma declaração de função quanto de uma expressão de função. Uma declaração de função é o modo normal de se criar uma função.

// Declaração de função
function myFunction() {}

De outro lado, se você atribuir uma função À uma variável ou propriedade, você estará lidando com uma expressão de função.

A razão principal para usar um IIFE é para ter as var privates . Isso porque o scopo das variáveis declaradas com var dentro de uma IIFE é restrito à ela e não podem ser acessadas de fora.

Uma IIFE pode ser usada para criar um  design pattern  conhecido como Módulo:

```

## Considerações 
1. https://github.com/Webschool-io/be-mean-instagram-artigos
2. padrão: artigo-instanciacao-githubuser-nome-completo.md
3. Pasta Variables

