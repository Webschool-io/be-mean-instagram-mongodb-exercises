# Como o ***JavaScript*** cria e instância as variáveis.

### Autor **: Tiago Nunes(TiagoWinehouse)**

### O que são variáveis?
- São endereços de memória nos quais podemos armazenar, recupear e manipular valores que aparecem no código.

```javascript
	var x = 10;
	var minhaVariavel = 'Minha Variável';
```

- Criando uma variável ***automaticamente***, sem que antes ela tenha sido declarada.

```javascript
	var x = 10;
	var y = 2;
	z = x + y;
//(x e y) foi declarada e a variável (z) foi criada automaticamente para receber a soma de x e y;
```

- Criando uma variável com apenas a instrução ***var*** (sem da um valor para ela), o seu resultado será ***undefined*** ou ***NaN(Not a Number, nã é um número)***.

```javascript
	var x ;
	x = x + 3;
// resultado será NaN
```
```javascript
	x = x * "Flamengo";
// o resultado não será o melhor time do mundo e sim, erro de execução, pois o x não foi definido.

```
- Criando uma variável **Pública** ***[Caso a variável seja declarada fora do coprpo de uma função]***.

```javascript
	var x = 10;
	function fx(){/* Assim será possível utilizar o valor de x */}
	function fy(){/* Assim será também possível utilizar o valor de x */}
```

- Criando variável **Privada** ***[Caso variável seja declarada dentro do corpo da função]***.

```javascript
	function fx() {
    var x = 5;
    /* será possível utilizar o valor de x */
    }
function fy() {/* x terá valor undefined, ou seja, não será visto por fy */}
```

- Criando variáveis **Constantes** ***[São declaradas com a palavra chave 'const', assim não podem sofrer alteração no seu conteúdo e nem de sua declaração no escopo]***.

```javascript
	const fs = 121;
	const time = "Flamengo";
// Se tentar alterar a sua declaração, ocorrerá um erro de execução.
```

- Criando variáveis que incluem **vetores** e **matrizes**.

```javascript
	var times = ["flamengo", "sergipe", "amg"];
	var nomes = new Array("Mara", "Carlos", "Lincon");
	var valores = [1.124, 3.1, 50, 13.14];
```

## Hoisting

- Declarações de variáveis são um aspectos dos mais básicos de qualquer linguagem de programação. No entanto, JavaScript tem um pouco de peculiaridade,  conhecido como ***Hoisting***, palavra em inglês que significa *"elevar"*, *"elevação"* ou *"içar"*.

Considere o seguinte código:

```javascript
	var meuvar = 'meu valor'; 
	alert(meuvar); // meu valor
```

É obvio, que o alert será exibido com o valor da variável passada no paramentro. Vamos para o proximo código, vamos criar uma função imediata, que vai fazer um alert com o mesmo valor.

```javascript
	var meuvar = 'meu valor'; 
	(function() { 
  	alert(meuvar); // meu valor 
	})();
```

Ainda é óbvio que será exibido o alert com a variável passada no paramentro. Agora, vamos jogar uma chave e criar uma variável local dentro dessa função anônima de mesmo nome.

```javascript
	 var meuvar = 'meu valor'; 
	(function() { 
  	alert(meuvar); // undefined 
 	 var meuvar = 'valor local'; 
	})();
```
A variável meuvar(local), meuvar foi declarada e automaticamente ela foi hasteada no topo do escope da função acima do alert. Com o resultado, a variável já tinha sido declarada no momento do alert. Por isso quando as inicioções são *hoisted* assim, o valor da variável é *undefined*.

## Closure

- Closures (fechamentos) são funções que se referem a variáveis livres (independentes).*https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Guide/Closures*

Em JavaScript, se criamos uma função dentro de outra função, estamos criando uma *closure*. Nas linguagens mais comuns, depois que uma função retorna todas as variáveis locais, elas não são mais acessíveis porque a stack-frame é destruida. Tendo isso em mente uma closure é considera como uma stack-frame que não é descocada quando a função retorna. Vamos da uma olhada no seguinte código:

```javascript

	function time(nome) {
    var texto = 'Eu sou ' + nome; // variável local
    var timeAlert = function() { alert(texto); }
    return timeAlert;
}
```
Vamos chamar a função da seguinte maneira:

```javascript

var time_ = time("Flamengo");
	time_();
}
```
A função time() retorna um ponteiro para a funcção timeAlert().

 * Aqui quando vc declara uma função dentro de outra função, as variáveis locais podem permanecer acessível após o retorno da função que ligamos. Isto é demostrado acima; nós chamamos a função *time_()* depois de ter retornado de *time()*.

## Variável Global

-  São aquelas que são criadas fora das funções, mas, que podem ser usadas, tanto dentro, tanto fora de funções, em qualquer parte do documento, desse modo, as variáveis, que seram usadas em mais de uma função, ou em vários pontos do código. 

```javascript
	var myGlobal = "O Flamengo é um time global"; // Variável Global
    function timeLocal(){
    var myGlobal = "O Curinthias é um time local"; //Variável Local
    console.log("Local: " + myGlobal);
    }
    console.log("Global: " + myGlobal);
```


## Variável por parâmetro

- Valor concreto que substitui uma variável, geralmente um valor numérico.https://pt.wiktionary.org/wiki/par%C3%A2metro

Temos uma função que recebem 2 parâmetros:

```javascript
	function multiplicar(x, y){
    	return x * y;
    }
    
    multiplicar(5,5);
    //25
```

## Instanciação usando uma IIFE (Immediately Invoked Function Expressions)

- É uma função anônima que é criada e , em seguida, imediatamente chamada. Não é chamada de qualquer outro lugar, mas funciona apenar depois de ser criada.

```javascript
	(function(){
    return 10;
    });
    // retorna 10
```

- Também pode ser usada para proteger contra os efeitos involuntários de elevação

```javascript
    var v = 1;
    var getValue = (function(x) {
      return function() { return x; };
    }(v));
    v = 2;

    getValue(); // retorno 1
```

A vantagem de usar o IIFE, é a capacidade de passar objetos geralmente instanciado globalmente a função anônima de um IIFE, e em seguida, refenciar estes objetos globais no IIFE atravẽs de um âmbito local. O JavaScript procura primeiro por uma propriedade no âmbito local, e em seguida, ele vai todo o caminho até a cadeia, por ultimo parando no escopo local.

```javascript
    // Função anônima passando 3 parâmetro.
    function(window, document, $) {

     // Aqui, você pode fazer referência ao window, document, do objeto JQuery no âmbito local.

    }(window, document, window.jQuery); //São passado para a função anônima.

```

- Outro benefício do uso é o desempenho na ajuda com a otimização minification.

```javascript
    // Função anônima passando 3 parâmetro.
    function(w, d, $) {

     // Aqui, você pode fazer referência ao window, document, do objeto JQuery no âmbito local.

    }(window, document, window.jQuery); //São passado para a função anônima.

```

- Esse padrão IIFE permite  que os objetos globais que você está passando em sua IIFE fiquem visivel, sem você ter que deslocar até o fundo de um arquivo muito longo.

```javascript
	(function (library) {

    // Chama o segundo IIFE e localmente passa para o JQuery como objetos globais.
    library(window, document, window.jQuery);

}

    // Parâmetro local
    (function (window, document, $) {

    // Aqui o código!

    }));
```

## Referências Bibliográficas

https://developer.mozilla.org/pt-BR

https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Guide/Closures

https://developer.mozilla.org/en-US/docs/Glossary/IIFE
