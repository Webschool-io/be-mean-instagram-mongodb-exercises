# Instanciação de variáveis no JavaScript

autor: Mauricio José Maria Ruiz Díaz Maciel

## Hoisting
  O JS, contrário ao que muitos acreditam, é uma linguagem compilada; compilada em momentos antes da execução. Por ende, ela tem varios mecanismos ou componentes que interagem no momento da compilação. Um destes mecanismos é o Scope que é o responsável por armazenar as referencias às varáveis. Na primeira etapa da compilação ela procura por todas as declarações dentro de cada bloco (como por exemplo dentro de uma função ou mesmo no entorno global) e as leva para o começo daquele bloco.

  Por tanto, um código como o seguinte ira funcionar sem problemas.

```
	function f(){
		console.log(a); //2
		var a = 2;
	}
```

  Mas o seguinte código ira dar um ReferenceError, pois a variável não foi declarada em momento nenhum dentro daquele bloco.
```
  	function(){
  		console.log(a);
  	}
```

## Closure
  Uma closure é, em termos simples, uma função que lembra o entorno dela mesmo após ter finalizado sua execução. Em outras palavras, o Scope daquela função continúa na memoria e continúa a ser referenciada se houver uma variável fora dela que referencíe um metodo ou variável interna. Uma utlização comum das Closure é no padrão de desenvolvimento modular, onde crião-se modulos que possuem metodos privados, dos quais alguns podem ser accesados por metodos publicos que referencíam ou lembram esses métodos privados. Dessa forma tambem os metodos privados podem executar funções ou rotinas internas, sem deixá-las expostas por fora da função.

```
	var api = function(){
		var i=0;
		function log(a){
  		console.log(a);
  		i++;
  	}

  	function print(a){
  		log(a);
  	}

  	return print;
  }

  var myApi = api();
  myApi.print(2);// console.log(2); i++;
  myApi.log(2);//ReferenceError
```

## Variável Global
  O sistema de Scopes, no JavaScript funciona encapsulando blocos de código para que somente as variaveis declaradas nesse mesmo Scope possam accesá-las. As variáveis dentro de um Scope podem, porém, referenciar variáveis existentes em Scopes superiores. No ultimo nível encontra-se o Scope Global, o Scope que está por cima de todos. Por este motivo, uma variável declarada no Scope Global pode ser referenciada dentro de uma função, sempre e quando não aconteçã o shadowing de uma variável (não exista uma variável com o mesmo nome nesse mesmo Scope), pois a procura de uma variável acontece desde o Scope atual e vai para os Scopes superiores, parando no momento em que ele encontra aquela variável sendo procurada.
  Obs.: Ao atribuir um valor a uma variável, se esta não é encontrada em nenhum Scope, ela é declarada no Scope Global (sendo esta uma má pratica, segundo varios desenvolvedores porque pode criar um funcionamento inadequado do script) a não ser que o 'strict mode' esteja ativado. Neste caso será dada uma ReferenceError.

```
	var a = 2;
	function f(){
		console.log(a); //imprime 2 porque como ele não encontra a variável a dentro da função, vai para o Scope superior, que é o Scope Global.
}

function b(){
	var a = 3;
	console.log(a); // imprime 3 porque existe uma variável a dentro daquele Scope, então a procura para dentro da função e não chega ao Scope Global.
}

function c(){
	a = 4; // a variavel global a recebeu o valor 4.
	b = 5; // foi criada uma variável com o nome b e recebeu o valor 5.
}
```

## Variável por parámetro
  Em JavaScript uma variável pode ser passada para uma função facilmente. Basta, na hora da instanciação da função deixar entre parentesis os parametros que ela irá receber, sem possibilidade de explicitar o tipo de variáveis que pode receber (isto da uma maior flexibilidade à linguagem segundo algúns desenvolvedores). Estas variaveis passadas como parametro passam a formar parte do Scope Lexico da função, por tanto, se referenciadas dentro da função, serão encontradas, sem necessidade de ir para outro Scope superior.

```
	function t(a){
		console.log(a);
}

t(2); // o valor 2 será impresso no console.
```

## Instanciação usando uma IIFE
  IIFE são as siglas de Inmediately Invoked Function Expression, são funções declaradas e invocadas ou executadas inmediatamente depois de ser instanciadas. Uma IIFE é comunmente utilizada para encapsular as variáveis e funções que se encontram dentro delas sem poluir o Scope Global, pois nenhuma referência é criada em ela. Mesmo assim, as IIFE's são funções, portanto podem receber valores por parametros como retornar valores que podem ser armazenados dentro de uma variável.

```

	var k = (function(a){
		function inc(){
  		a++;
  	}
  	function log(){
  		console.log(a);
  	}
  	// será retornado um objeto com referencias aos metodos internos, criando uma Closure por cima.
  	return {
  		inc : inc, // o atributo 'inc' referencia a função inc que existe dentro da função
  		print : log // não importa se o nome é diferente.
  	}
})(2); // a recebe 2. porém, ela não pode ser referenciada diretamente desde fora da IIFE

k.print(); // imprime 2 na consola.
k.inc(); // a é incrementado, recebe 3.

```