# Artigo Instanciação
**autor**: Rodrigo Alves Guerra

## Hoisting

### O que é ?

É a possibilidade de se declarar uma variável ou uma função em qualquer parte do seu código, 
sendo equivalente a declarar no início da função ou do código global.

### Porquê acontece ?

As variáveis e as funções são processadas antes que o código seja executado, 
possibilitando a declaração de uma variável ou função em qualquer parte do código.

### Como acontece com variável e função ?

Tendo em vista que no JavaScript as variáveis são processadas antes que o código seja executado, 
e são movidas para o inicio da função ou do código global.
Declarar uma variável em qualquer parte do seu código é equivalente a declarar no início da função ou do código global.
Até mesmo é possível utilizar uma variável antes dela ser declarada.

	Ex.

		var x; // declaração da variável x 

		x = 4;	// atribuindo valor 4 a variável x

		y = 3; // atribuindo valor 3 a variável y

		alert(x + y); // utilização das variáveis x ,y. Saída = 7

		var y; // declaração da variável y

		// È o mesmo que !

		var x; // declaração da variável x
		var y; // declaração da variável y

		x = 4; // atribuindo valor 4 a variável x

		y = 3; // atribuindo valor 3 a variável y

		alert(x + y); // utilização das variáveis x ,y . Saída = 7


## Closure

### O que é ?

É uma função que tem acesso a variáveis interiores e exteriores da função, 
e pode ter acesso a três cadeias de escopos, o escopo das variáveis globais, 
o escopo da função exterior dela, e o seu próprio escopo.

### O porquê acontece ?   

Para se obter valores de variáveis locais de uma função em qualquer parte do seu código. 
"Uma closure deixa você associar dados (do ambiente) com uma função que trabalha estes dados. 
 Isto está diretamente ligado com programação orientada a objetos,
 onde objetos nos permitem associar dados (as propriedades do objeto) utilizando um ou mais métodos."

### Como usar ? 

Você pode utilizar em qualquer lugar do seu código em que você utilizaria um objeto de único método.

## Variável Global

Variável que pode ser acessada em todos os escopos do seu programa.
	
	Ex. 

	var name = "rodrigo alves guerra";

	function escreve_nome(){
		var string = "Seu nome é :";
		console.log(string + name);			
	}

	escreve_nome();

	console.log("Bem Vindo, " + name);

No código acima, você percebe que a função 'escreve_nome' acessa a variável 'name', 
que não está no escopo dessa função, mas que é uma variável global ao código em questão.
Por isso é possível acessá-la dentro da função 'escreve_nome'.

## Variável por parâmetro

Parâmetro é uma referência a uma variável do código que é passada para uma função, 
seria uma cópia do conteúdo da variável que é transmitida para a função, 
podendo ser alterado o conteúdo do parâmetro na função sem alterar o conteúdo da variável.

	Ex. 

	var a = 4; // 'a' variável GLOBAL

	function quadrado(b){ // 'b' variável por Parâmetro 
		b =  b * b; // modificando variável 'b' 
		alert(b); // mostrando a modificação
		alert(a); // mostrando que a variável Global não muda			
	}

	quadrado(a); // passando variável Global por parâmetro

## Instanciação usando uma IIFE

IIFE  ou  função imediatas, a função é executada imediatamente depois de criada;

	Ex.

	(function () {
	  console.log('Olá Mundo !') // será executada imediatamente	
	}());

Uma IIFE pode retornar um valor para uma variável do código, 
mas uma variável declarada no escopo de um IIFE não pode ser acessada fora do escopo IIFE.
	
	Ex.

	var iife = (function() { 
		var string = "Sou um IIFE";
		return string; 
	})();

        alert(iife); // Saída "Sou um IIFE"
        alert(string); // Saída 

	

Passando Parâmetro para a IIFE.
	
	Ex.
	
	var escreve = (function () {
           return function (x){
	          return alert(x) // será executada 	
           }
	}());

        var resposta = prompt('o que quer escrever ?');
        escreve(resposta);
        var resposta = prompt('o que quer escrever ?');
        escreve(resposta);

Referência .: https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Statements/var ,  https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Guide/Closures , http://javascriptbrasil.com/2013/10/12/entenda-closures-no-javascript-com-facilidade/ , https://pt.wikipedia.org/wiki/Vari%C3%A1vel_global , http://imasters.com.br/front-end/javascript/sobre-funcoes-imediatas-javascript-iife/ .
