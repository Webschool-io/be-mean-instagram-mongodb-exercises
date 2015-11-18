# Instanciação de variáveis no JavaScript

autor: Marcos Antonio Martinez Florentin

## Explique, com teoria e código, nesse artigo como o JavaScript cria e instancia as variáveis, seguindo os seguintes tópicos.
o JS, ele cria uma variavel com a palabra reservada var, no JS no existe tipo de variaveis mas existem tipos de dados

## Hoisting
  Hoisting se refere cuando una uma declaracao de variavel e levada au inicio de um block de codigo por exemplo ao inicio de uma funcao 
```
	function (){
	console.log(a);
	var a = 'cualque coisa';	
	}

```
## Closure
closure sao funcoes que tei variaveis independentes. En otroas palabras, as funcoes definida no closure "relembra" o entorno en que se  foi criado

```
	function inicia() {
	  var nome = "Nome"; // 'nome' e uma variavel local creada por funcoes iniciada' 
	  function nosoNome() { // 'nosoNome' e uma funcao interna (um closure)
	    alert(nome); // dentro de esta funcao usamos uma variavel declarada na funcao Pai 
	  }
	  nosoNome();
	}
	inicia();  
	
```

## Variável Global
 As variaveis glabais estao nos datos de propiedades de un objeto global. Nos Sites o Objeto global e window, pode establecer e acceder a variaveis globais usando a sintaxis windows.variavel.

Por tanto pode acceder a variavel global declarada em uma janela ou frame de otra janela ou frame especificando o nome da janela ou frame. Por exemplo si uma variavel denominada phoneNumber e declarada en un documento, podera consultara uma variavel a partir de um iframe como parent.phoneNumber.
```
	var a = 'variavel global';
	function (){
	console.log(a);
	}
	
```

## Variável por parámetro
  Os Parametros se usam para mandar valores para as funcoes. Uma funcao trabalhara com os paramentros para realizar as acoes.
Ao usu do paramentro en noso programa javascript, temos que saber que os paramentros de funcoes se pasan por valor.Isto quer dicer que estamos  pasando valores y nao variaveis. Na pratica, si modificamos un parametro en uma funcao, a variavel original que tiamos pasado nao mudara o valor. se puder ver facilmente no exemplo  
```
	function escreberBomDia(nome){ 
   	document.write("<H1>Hola " + nome + "</H1>") 
	s}
```

## Instanciação usando uma IIFE
IIFE (Inmediately Invoked Function Expression) basicamente se utiliza para aislar  os codigos(funcoes y variaveis), para nao poluir  o entorno global programando com un entorno de desenvolvimento modular,
donde existe uma "api" publica y uma que se conserva privada 

```
	var v = (function(m){
	function printMsg(){
	console.log(m);
	}
	return {
	print : printMsg
	}
	})('oi');

```
