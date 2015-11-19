Artigo - Instanciação Javascript
Aluno: Tiago Amado Durante

# Hoisting
Em javascript, quando uma variável é declarada, pode se dizer que esta variável foi hoisted. Em outras palavras, a declaração desta variável foi elevada acima do escopo, antes mesmo que fosse executado o codigo. Lembrando que, é apenas elevado acima do escopo a sua declaração e não sua inicialização.

Exemplo de hoisting com variável:
Neste exemplo, a variavel 'aux' não foi definida, fazendo com quem caia no catch e exiba o erro.
  try {
    console.log(aux);
  } catch(exception) {
    console.error('aux is not defined');
  }

Neste outro exemplo, 'aux' foi definido após o metodo que exibe no console. Mesmo que tenha sido definida após a chamada, ela se torna hoisted e passa a ficar acima do escopo, antes mesmo do sistema executar, alterando o resultado do try:
  try {
    console.log(aux); //undefined
    var aux;
  } catch(exception) {
    console.error('aux is not defined');
  }

Como detalhe abordado, quando a variável se torna hoisted, apenas sua declaração fica acima do escopo, sua inicialização não sofre qualquer tipo de ação:s
  try {
    var aux;
    console.log(aux); //undefined
    aux = 2015;  
  } catch(exception) {
    console.error('aux is not defined');
  }

No caso das funcões, seu funcionamento será parecido.
  console.log(exibirInformacoes()); //Tiago Amado Durante - Aluno da Webschool.io
  function exibirInformacoes() {
    return 'Tiago Amado Durante' + ' - ' + 'Aluno da Webschool.io'
  }

Em um exemplo onde exista 2 metodos declarados com o mesmo nosme, permanecerá acima do escopo o ultimo que for declarado.
  function exibirInformacoes() {
    function nome() {
      return 'Tiago'
    }

    return nome()

    function nome() {
      return 'Tiago Amado Durante'
    }
  }

  console.log(exibirInformacoes());

# Closure
Closure se resume a uma função interior onde ela tem acesso ao seu próprio escopo, ao escopo da função externa a qual ela foi declarada (variaveis e parâmetros) e ao escopo global. Fato é que, após ser executada, a closure ainda tem acesso as variaveis das funcões exteriores, podendo ser chamada posteriormente em seu programa. Outra caracteristica interessante é que uma closure pode armazenas valores em variáveis sem alterar o valor original.

//codigo de um sistema que estou desenvolvendo
angular.module('fazendatec').factory('Vaca', function($resource){
	return {
		vaca : $resource('/vacas/:id'),
		vacaByCodigo : $resource('/vaca/codigo/:codigoVaca')
	}
});

# Variável global em uma função
Uma variável global dentro de uma função pode ser declarada desde que não esteja dentro de outra função interna, permitindo que as demais funções internas tenham acesso ao seu valor, seja para alterar ou exibir.
function minhaInfo() {
  var nome = 'Tiago Amado Durante'; //variavel global

  function exibirNomeComIdade() {
    return nome + ', tenho 22 anos.'
  }

  console.log(exibirNomeComIdade());
}

# Variável por parâmetro
Quando uma variável é passado por parâmetro em uma função, seu valor passa a ser usado dentro de um novo contexto, diferente do qual ela foi declarada. No caso do javascript, ainda é possivel que voce chame determinada função passando seu nome por parâmetro.

function meuNome(nome) {
  console.log(nome);
}
function executar(funcao, valor) {
  funcao(valor);
}

executar(meuNome, "Tiago Amado Durante");

# Instanciação usando uma IIFE
Conhecida também como função imediata, a Immediately-invoked function expression é uma função que é exeutada logo após ser criada. O objetivo das IIFE é criar um escopo temporário para que possa trabalhar com funções e variáveis, evitando assim a poluição do escopo global do sistema e alguns possiveis conflitos de nomes de variáveis ou de funções com o mesmo nome. IIFE pode também ser usado para criar variáveis privadas, já que elas ficaram disponíveis apenas escopo da função.

(function doSomething() { #codigo# })(); // undefined

// Agora com função anônima
(function() {  #codigo#  })(); // undefined

Uma variável pode receber o valor de uma IIFE desde que exista um retorno dentro da função, e que ela seja declarada logo após declararmos a variável que receberá o valor:
  var conte = (function () {
    var numero = 0;

    return function () {
      numero = numero + 1

      return numero
    }
  }())

  conte() // 1
  conte() // 2
  conte() // 3
  conte() // 4

Para passarmos algum valor a uma IIFE, devemos colocar o valor em questão entre os dois parenteses localizados no final da função:
  (function (string) {
    console.log(string) // Log 'Tiago Amado Durante'
  }('Tiago Amado Durante'))

# Referêcias
http://tutsmais.com.br/blog/javascript-2/o-que-e-iife-no-javascript/
http://imasters.com.br/front-end/javascript/sobre-funcoes-imediatas-javascript-iife/
http://javascriptbrasil.com/2013/10/12/entenda-closures-no-javascript-com-facilidade/
http://loopinfinito.com.br/2014/10/29/hoisting-e-escopo-em-javascript/
http://nodebr.com/passando-funcao-como-parametro-no-javascript-com-node-js/
