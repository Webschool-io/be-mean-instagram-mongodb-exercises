# Instanciação de variáveis no JavaScript

autor: Andrew Esteves

## Hoisting
  Hoisting em sua tradução para o português significa "içada" e este comportamento no JS é no qual as variáveis podem ser declaradas após sua utilização. Isto ocorre pois o JS "iça" ou "levanta" todas as declarações para o começo do bloco em execução, por este motivo temos este termo Hoisting.

```
	x = 7; // Atribuindo
  console.log(x);
  var x; // Declarando

```

## Closure
  Closure ou "encerramento" é uma função que tem acesso as variáveis do seu ambiente de criação.
  São bastante utilizados na criação de modulos que possuem metódos e/ou atributos privados.

```
	function ligar() {
  var carro = "Jaguar";
  function acelerar() {
    console.log('Acelerando o ', carro);
  }
    acelerar();
  }
  ligar();
```

## Variável Global
  A variável global é acessível tanto de dentro de uma função como também estando fora dela.
  O funcionamento é através de enpsulamento dos blocos, liberando ou não o acesso das variáveis. O acesso é iniciado de dentro para fora, caso haja uma variável com o mesmo nome dentro da função e outra fora o JS irá utilizar a variável de escopo local ao invés do global.

```
  var x = 7;
  function a(){
  		console.log(x); // x == 7
  }

  function b(){
  	var x = 5;
  	console.log(x); // x == 5
  }

  function c(){
  	x += 3; // x == 10.
  }
```

## Variável por parâmetro
  São as variáveis listadas na definição da função. O valor atribuído as estas variáveis são chamadas de "argumentos".
  Possuem escopo local ao de sua função onde podem ser acessadas.
  Para definir a variável pelo parâmetro basta informar dentro dos parênteses. 
  Ex.:
```
  function foo(parametro1, parametro2) { // bloco de código };
```

```
	function a(b, c){
		console.log(b, c);
}

a(1, 2); // b == 1 && c == 2
```

## Instanciação usando uma IIFE
  A instanciação de uma função utilizando IIFE (Inmediately Invoked Function Expression) já invoca a mesma logo após ser instanciada, funções auto executáveis.
  Utilizadas para evitar "hoisting" nas variáveis e proteger o escopo global mantendo-o limpo, ao mesmo tempo permitindo acesso público aos metódos e mantendo a privacidade das variáveis definidas dentro das funções.

```
  (function() {
    // Código a ser auto executado
  }());

  // Utilizando parâmetro
  (function(js) {
    // js == Javascript
  }('Javascript'));

  // Utilizando variável privada e acessos
  var counter = (function(){
  var i = 0;
  return {
      get: function(){
        return i;
      },
      set: function(value){
        i = value;
      },
      increment: function() {
        return ++i;
      }
    };
  })();
  counter.get(); // 0
  counter.set(7);
  counter.increment(); // 8
  counter.increment(); // 9
```