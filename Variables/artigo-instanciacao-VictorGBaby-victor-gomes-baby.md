# Artigo - Instanciação em Javascript
**autor**: Victor Gomes Baby

Criação e instanciação de váriaveis através de Hoisting, Closure, Váriavel Global, Variável por parâmetro e Instanciação usando uma IIFE.

## Hoisting

Quando declaramos uma várivavel ou função sua declaração é elevada para o topo do escopo. Mesmo existindo diferentes métodos de declaração de entrada no escopo há uma diferença na ordem  de resolução, alguns podem ser resolvidos primeiro mesmo aparecendo no fim do escopo enquanto outros podem ter apenas seus nomes resolvidos, sem terem seus valores inicializados.
Toda variável que é definida tem sua declaraçao  hoisted, mas não sua inicialização, o que quer dizer que a declaração da variável vai para cima do escopo antes mesmo do código ser executado.

#Code

 -- Com variáveis
x = 5; // Assign 5 to x

elem = document.getElementById("demo"); // Find an element 
elem.innerHTML = x;                     // Display x in the element

var x; // Declare x

-- Com função
foo()
function foo() {
  console.log('bar')
}


## Closures

Closure é uma função interior que tem acesso a variáveis de uma função exterior, nested functions, ele tem três cadeias	de escopo, ele tem acesso ao seu próprio escopo (variáveis definidas entre suas chaves), as variáveis da função exterior e tem acesso as variáveis globais.
Ela tem acesso não só as variáveis mas também aos parâmetros da função exterior, mas não pode chamar eles diretamente.
Você cria uma closure adicionando uma função dentro da outra.

#Code
function showName (firstName, lastName) {
    var nameIntro = "Your name is ";
 
    //esta função interior tem acesso as variáveis da função exterior, incluindo os parâmetros
    function makeFullName () {
        return nameIntro + firstName + " " + lastName;
    }
 
    return makeFullName ();
}
 
showName ("Michael", "Jackson"); //Your name is Michael Jackson

## Variáveis globais dentro de uma função
Variáveis globais são declaradas fora de uma função no escopo global. Uma ver declarada ela pode ser usada normalmente dentro e fora de qualquer função.

##Code
var age;
function showAge() {
    //age é uma variável global porque ela não foi declarada com a palavra chave var dentro da função
    age = 90;
    console.log(age); 
}
 
//age está no contexto global, então está disponível aqui, também
console.log(age); //90

## Variável por parâmetro
Quando uma variável é passada como parâmetro para uma função, é como se fosse uma nova variável ou seja as alterações feitas dentro do escopo dessa função somente serão visíveis no próprio escopo. Caso seja passada uma variável GLOBAL como parâmetro o mesmo acontece.
O valor das variáveis passadas como parâmetro somente irão receber o valor alterado dentro da função caso as mesmas sejam retornadas por referência. Assim o ponteiro da memória onde está sendo alterado os valores não é trocado para um ponteiro novo.

#Code
function passoPorValor(meuParametro){ 
   	meuParametro = 32 
   	document.write("mudei o valor a 32") 
} 
var minhaVariavel = 5 
passoPorValor(minhaVariavel) 
document.write ("o valor da variavel e: " + minhaVariavel) 

No exemplo, temos uma função que recebe um parâmetro, e que modifica o valor do parâmetro atribuindo-lhe o valor 32. Também temos uma variável, que iniciamos a 5 e posteriormente chamamos à função passando esta variável como parâmetro. Como dentro da função modificamos o valor do parâmetro poderia acontecer da variável original mudasse de valor, mas como os parâmetros não modificam o valor original das variáveis, esta não muda de valor. Deste modo, ao imprimir na tela o valor de minhaVariavel se imprimirá o número 5, que é o valor original da variável, no lugar de 32 que era o valor col o que havíamos atualizado o parâmetro. 

## Instanciação usando uma IIFE
IIFE significa "Immediately-invoked function expression" e ela é utilizada para encapsularmos o escopo no javascript de uma forma que as declarações globais não venham a interfirir no que está dentro dela. Sua execução é feita na declaração.

#Code
function MyApp() {
  if (!MyApp.instance) {
    MyApp.instance = this;
  }

  return MyApp.instance;
}

Essa função construtora irá garantir que você sempre receba a mesma instância como resultado. Isso só é possível porque funções construtoras utilizam o retorno como resultado da instanciação. Na prática, você poderia retornar qualquer tipo de objeto, como arrays ou strings.
Desta forma, uma variável só pode receber um valor utilizando o return dentro da função imediata, onde conseguimos exportar algum resultado que foi processado.

## Referências
http://loopinfinito.com.br/2014/10/29/hoisting-e-escopo-em-javascript/
http://www.w3schools.com/js/js_hoisting.asp
http://javascriptbrasil.com/2013/10/12/entenda-closures-no-javascript-com-facilidade/
http://javascriptbrasil.com/2013/10/11/escopo-de-variavel-e-hoisting-no-javascript-explicado/
http://www.criarweb.com/artigos/233.php
https://nandovieira.com.br/design-patterns-no-javascript-singleton
