# Artigo
**autor**: Rodrigo Alves Guerra

**Prazo**: até dia 18 de Novembro de 2015

Explique, com teoria e código, nesse artigo como o JavaScript cria e instancia as variáveis, seguindo os seguintes tópicos.

## Hoisting

### O que é ?

É a possibilidade de se declarar uma variável em qualquer parte do seu código, 
sendo equivalente a declarar no início da função ou do código global.

### Porquê acontece ?

As variáveis são processadas antes que o código seja executado, 
possibilitando a declaração de uma variável em qualquer parte do código.

### Como acontece com variável e função ?

Tendo em vista que no JavaScript as variáveis são processadas antes que o código seja executado, 
e são movidas para o inicio da função ou do código global.
Declarar uma variável em qualquer parte do seu código é equivalente a declarar no início da função ou do código global.
Até mesmo é possível utilizar uma variável antes dela ser declarada.

	Ex.

		var x;

		x = 4;

		y = 3;

		alert(x + y); 

		var y;

		// È o mesmo que !

		var x;
		var y;

		x = 4;

		y = 3;

		alert(x + y); 


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

Vocẽ pode utlizar em qualquer lugar em que você ultilizaria um objeto de único método.

### Em que situações que você usaria ?


## Variável Global

Variável que pode ser acessada em todos os escopos do programa de computador.
	
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
Por isso é possível acessala dentro da função 'escreve_nome'.


### Explique como se usa uma var Global dentro de uma função.

## Variável por parâmetro

Explique o que acontece dentro da função qnd um parâmetro é passado e também explique quando uma GLOBAL é passada por parâmetro.

Parâmetro é uma referência a uma variável do código que é passada para uma função, 
seria uma cópia do conteúdo da variável que é transmitida para a função, 
podendo ser alterado o conteúdo do parâmetro na função sem alterar o conteúdo da variável.


## Instanciação usando uma IIFE

Explique como uma variável pode receber um valor de uma IIFE.
Explique como passar uma variável por parâmetro para a IIFE e acontece com ela dentro da função.


Referência .: https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Statements/var ,  https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Guide/Closures , http://javascriptbrasil.com/2013/10/12/entenda-closures-no-javascript-com-facilidade/ , https://pt.wikipedia.org/wiki/Vari%C3%A1vel_global 
