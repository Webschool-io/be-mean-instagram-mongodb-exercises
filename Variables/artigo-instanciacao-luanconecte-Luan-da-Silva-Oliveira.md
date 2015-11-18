# Artigo
**autor**: Luan da Silva OLiveira

Explique, com teoria e código, nesse artigo como o JavaScript cria e instancia as variáveis, seguindo os seguintes tópicos.

## Hoisting

--------
Todas declarações de variáveis são hasteadas (levantadas e declaradas) no topo da função, se definida dentro da função, ou no topo do contexto global, se usada fora de uma função.

É importante saber que somente declarações de variáveis são hasteadas ao topo, não a inicialização de variáveis ou atribuições (quando para uma variável é atribuído um valor).

named();

function named() {
	console.log(name);
}

var name = "Luan Oliveira";

No exemplo a cima a declaração da variável name e a função named são hasteadas para o inicio do escopo que nesse caso é global;
--------

## Closure

Explique o que é, o porquê acontece e como usar. 
Cite situações que você usaria.

## Variável Global

Explique como se usa uma var Global dentro de uma função.

--------
Variáveis locais são definidas dentro de uma função e só podem ser acessadas dentro do seu escopo. Já as variais globais são definidas fora de funções e pertencentes ao obcject window.

Uma variável global pode ser usada dentro de uma função normalmente, como:

// variável global
var name = "Luan Oliveira";

function foo() {
	// chamando a variável global
	console.log(name);
}
--------

## Variável por parâmetro

Explique o que acontece dentro da função qnd um parâmetro é passado e também explique quando uma GLOBAL é passada por parâmetro.

--------
Ao passar um parametro ou definir um parêmetro com o mesmo nome de uma variável global  em uma determinada função, é criada uma nova varária local, ou seja, restrita ao interior da propria função.

var name = "Luan Oliveira";

function named(name) {
	console.log(name);
}

// imprime a variável local passada por parâmetro dentro da função named
named("Luan");
--------

## Instanciação usando uma IIFE

--------
Evitar variáveis globais é uma forma de deixar o código menos confuso e a prova de erros, com isso o IIFE (Immediately-Invoked Function Expression) veio como uma forma de "isolar" um bloco de código envolvido entre ( ) do escopo global. Eles basicamente retornam qualquer coisa que pode ser definida em seu interior.

//variavel mongodb não é acessível no escopo global
(var mongodb = "oi")

//varivel mongodb com o seu valor atribuído através de um IIFE
var mongodb = (function () { return 'oi' })

Utilizando um segundo parentese ao final da declaração é possível passar uma variavel ou uma lista de variáveis que serão referenciadas por atributos dentro da função invocadora. Também é importante lembrar que mesmo passando uma variável global dentro do IIFE será criada uma variável local.

(function(name) {
	console.log(name);
})("Luan Oliveira");

var name = "Luan Oliveira";

(function(name) {
	name = "Truta";
	console.log(name);
})(name);

console.log(name);

Isso vai imprimir:
// Truta
// Luan Oliveira
Porque não altera o escopo global da variável name;
--------