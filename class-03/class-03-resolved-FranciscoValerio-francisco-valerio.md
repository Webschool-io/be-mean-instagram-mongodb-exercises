# MongoDB - Artigo
autor: **Francisco Henrique Ruiz Valério**

## Hoisting

Em JavaScript, uma variável/função pode ser declarada depois de ter sido usada.
Hoisting é um comportamento padrão de JavaScript de mover todas as declarações para o topo do escopo atual (para o topo do script atual ou a função atual).

Exemplo:

<!DOCTYPE html>
<html>
	<body>

	<p id="hoisting"></p>

	<script>
		myHoisting();
	
		function myHoisting(){
			x = 25; // Inicializando 25 para x

			element = document.getElementById("hoisting"); // procurando um elemento
			element.innerHTML = x;                         // mostrando x no elemento

			var x; // Declarando a variavel x
		}
	</script>

	</body>
</html> 

## Closure

Variáveis de JavaScript	podem pertecer ao escopo **GLOBAL** e **LOCAL**.

Variável com escopo LOCAL: A função pode acessar todas variáveis definidas dentro dela, ou seja outra função e/ou uma windows object não tem acesso a essa variável.
Exemplo:

function sampleVariableLocal() {
    var z = 6; // isto e uma variavel local
    return z * 2;
}

Variável com escopo GLOBAL: É a variável declarada fora de qualquer função, com isso a mesma fica visível para qualquer função do script como para a windows object também.
Exemplo:

var a = 2; // isto e uma variavel global
function sampleVariableGlobal(valor) {
    return valor * a;
}

**Observação: Variáveis criadas sem a palavras VAR, são sempre globais, mesmo sendo criadas dentro de uma função.**

	
## Variável Global

Uma variável **GLOBAL** pode ser usada dentro de uma função como se fosse uma variável qualquer, lembrando que ao alterar o valor dessa variável em um função para o restante do código aquela variável estará com o seu valor alterado.
Exemplo de uso:

var nome = "Francisco Valério";

function retornaAutor(){
	return 'Autor: ' + nome;
}


## Variável por parâmetro

Quando uma variável é passada como parâmetro para uma função, é como se fosse uma nova variável ou seja as alterações feitas dentro do escopo dessa função somente serão visíveis no próprio escopo. Caso seja passada uma variável GLOBAL como parâmetro o mesmo acontece.
O valor das variáveis passadas como parâmetro somente irão receber o valor alterado dentro da função caso as mesmas sejam retornadas por referência. Assim o ponteiro da memória onde está sendo alterado os valores não é trocado para um ponteiro novo.

## Instanciação usando uma IIFE

IIFE geralmente ficam dentro de parênteses (), o que eles fazem basicamente é retornar qualquer coisa que você coloque dentro dele, como se fossem parâmetros de uma função.
var funcao = function () { return 'oi' }(); 

Uma variável pode receber o valor de uma IIFE apenas pelo seu retorno/resultado. 

Para passar um parâmetro para uma IIFE basta utilizar o segundo parâmetro da mesma ou seja:
Outra coisa interessante é que no segundo parênteses, onde invocamos a function, podemos passar qualquer parâmetro como se fosse qualquer outra função.

( function (string) {
  console.log( string )
}( 'teste' ) )
 
//resultado Log: 'teste'

Você deve usar uma IIFE sempre que surgir a necessidade de isolar as variáveis que você precisa do escopo global. 
Isso é uma boa prática e é uma forma de fazer com que seu código funcione bem independente de onde ele for usado.


























