##Instanciação com Javascript  
#####Diego Araújo


##Resumo

Neste artigo falaremos sobre algumas funcionalidades do JavaScript como hoisting, closure, tipos de variáveis e IIFE; usaremos alguns códigos e conceitos retirados de outros artigos como exemplo para melhor entendimento do leitor.

##Palavras-chave
Javascript, Hoisting, Closure, Variáveis.

##Hoisting

Hoisting se traduzido literalmente significa: levantar algo através de algum meio, em JavaScript quando declaramos uma variável ou função ela sobe para o topo do escopo.  

>//Primeiramente vamos tentar imprimir no console uma variável que não foi declarada  
>try {  
>  console.log(a)  
>} catch (e) {  
>  console.error('A variável `a` não foi definida.')  
>}  
>//Essa "declaração" irá retornar um erro pois a variável não existe.  
>// Agora declarando uma variavel que sera chamada antes de sua instanciação  
>try {  
>  console.log(a)  
>  var a = 2  
>} catch (e) {  
>  console.error('A variável `a` não foi definida.')  
>}  

Neste caso o console retornará "undefined", pois a variavel foi declarada mas não instanciada, este é um exemplo básico de hoisting com variáveis.
Nas funções tudo ocorre um pouco diferente, pois o nome e o corpo da função serão "hoisteados" quando esta for declarada.

>//Chamando uma função antes da sua instanciação  
>foo()  
>function foo() {  
>  console.log('bar')  
>}  

Neste caso o console não imprimirá erros, pois, como foi dito a função e seu corpo são hoisteados na sua declaração.

##Closures

"Closures(fechamentos) são funções que se referem a variáveis livres(independentes)." (2015, https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Guide/Closures).  
As closures nos permitem associar dados com uma função que usará tais dados(tal como na orientação a objetos), onde os objetos por sua vez nos permitem associar dados utilizando métodos.
Usaremos um exemplo de um artigo do site Developer Mozilla.  

>function makeSizer(size) {  
>  return function() {  
>    document.body.style.fontSize = size + 'px';  
>  };  
>}  

Uma das utilidades das closures no JavaScript é emular métodos privados, ou seja criar métodos que só poderão ser chamados por outros métodos que estejam dentro da mesma classe. Obviamente a utilidade desse tipo de declaração é para criar restrições de acesso ao código, de forma que determinados métodos não fiquem "soltos" no nosso código.

>"var makeCounter = function() {  
>  var privateCounter = 0;  
>  function changeBy(val) {  
>    privateCounter += val;  
>  }  
>  return {  
>    increment: function() {  
>      changeBy(1);  
>    },  
>    decrement: function() {
>      changeBy(-1);  
>    },  
>    value: function() {  
>      return privateCounter;  
>    }  
>  }  
>};  
>var Counter1 = makeCounter();  
>var Counter2 = makeCounter();  
>alert(Counter1.value()); /* Alerts 0 */  
>Counter1.increment();  
>Counter1.increment();  
>alert(Counter1.value()); /* Alerts 2 */  
>Counter1.decrement();  
>alert(Counter1.value()); /* Alerts 1 */  
>alert(Counter2.value()); /* Alerts 0 */".

(2015, https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Guide/Closures).

##Variável Global

No JavaScript temos dois tipos de variáveis: Global e local. As variáveis globais são aquelas que foram declaradas fora de uma definição/escopo de função, seu valor e propriedades ficam acessíveis em todo o escopo do seu código(o que pode ser perigoso).

>var global = "Eu sou uma variavel global"; // variavel global  
>function varLocal () {  
>  var global = "Eu sou uma variavel local"; // variavel local  
>  console.log(global);  
>}  
>document.write(varLocal);  

No exemplo acima será impresso no console "Eu sou uma variável global" e logo abaixo "Eu sou uma variável local". Apesar das variáveis terem o mesmo nome elas não são a mesma variável, pois uma esta no escopo de variavel global e a outra no escopo de variavel local. Desse modo a variavel "global" que está dentro do corpo da função "varLocal" só poderá ser acessada através dessa função.

## Variáveis por parâmetro

Em Javascript é comum encontrarmos funções que recebem alguns parametros especificos, como por exemplo:  

>function variaveisPorParametros(parametro1, parametro2 parametro99999) {  
>  somaParametros = parametro1 + parametro2 + parametro99999;  
>  return somaParametros;  
>}

Para utilizar essa passagem de variaveis por parametros, existem algumas regras básicas, são elas:

1 - As definições das funções em JavaScript não especificam os tipos de dados para os parametros.  

>// procure usar nomes de parametros sugestivos  
> function somaNumeros(num1, num2){  
>  total = num1 + num2;  
>  return total;  
>}  
>var a = 10;  
>var b = 15;  
>somaNumeros(a, b);  
>// o resultado será 25  

2 - As funções em JavaScript não executam verificação de tipo(integer, float, boolean, etc) sobre os argumentos passados.  

>// se instanciarmos variaveis com tipos diferentes do esperado não receberemos o resultado esperado  
> function somaNumeros(num1, num2){  
>  total = num1 + num2;  
>  return total;  
>}  
>var a = "Teste";  
>var b = "Soma";  
>somaNumeros(a, b);  
>// o resultado sera "TesteSoma"

3 - As funções em JavaScript não verificam o número de argumentos recebidos.  

> function somaNumeros(num1, num2){  
>  total = num1 + num2;  
>  return total;  
>}  
>var a = 10;  
>somaNumeros(a);  
>// o resultado sera um erro NaN  

Isso acontece porque quando uma função é chamada e algum argumento está faltando, este argumento será setado por padrão como undefined(o que no exemplo explica o erro pois um numero não pode ser somado com undefined), no caso oposto, quando existem mais parametros do que os esperados, os parametros que excedem são desconsiderados.

>function somaNumeros(num1, num2){  
>    total = num1 + num2;  
>    return total;  
>}  
>var a = 10;  
>var b = 20;  
>var c = 30;  
>somaNumeros(a, c, b);  
>// o resultado será 40 pois a função irá considerar apenas os dois primeiros parametros  

## Instanciação usando IIFE

IIFE ou immediately-invoked function expression é um design pattern de JavaScript que produz um escopo lógico usando o escopo de função do Javascript, as expressões IIFE são usadas para evitar o hoisting das variáveis que estão dentro dos blocos das funções, proteger a poluição do escopo global do código e simultaneamente permitir o acesso a métodos públicos mantendo a privacidade das variáveis definidas dentro das funções.
Expressões IIFE podem ser escritas de várias maneiras, porém existe uma convenção comum em colocá-las dentro de parenteses:  

Usabilidade:

>var v, getValue;  
>v = 1;  
>getValue = function() { return v; };  
>v = 2;  
>getValue(); // 2  

Enquanto o resultado pode parecer óbvio ao atualizar v manualmente , ele pode produzir resultados indesejados quando getValue () é definido dentro de um loop.  

>var v, getValue;  
>v = 1;  
>getValue = (function(x) {  
>  return function() { return x; };  
>})(v);  
>v = 2;  
>getValue(); // 1  

Aqui, a função passa v como um argumento e é invocado imediatamente , preservando contexto de execução da função interna.
IIFEs também são úteis para o estabelecimento de métodos privados para funções acessíveis enquanto ainda expor algumas propriedades para uso posterior. O exemplo a seguir vem do post de Alman em IIFEs.  

>var counter = (function(){  
>  var i = 0;  
>  return {  
>    get: function(){  
>      return i;  
>    },  
>    set: function( val ){  
>      i = val;  
>    },  
>    increment: function() {  
>      return ++i;  
>    }  
>  };  
>})();  
>// 'counter' é um objeto que neste caso deverá ser  
>// métodos  
>counter.get(); // 0   
>counter.set( 3 );   
>counter.increment(); // 4  
>counter.increment(); // 5  

Se tentarmos acessar counter.i do ambiente global , ela será indefinida como se situasse no interior da função chamada e não como uma propriedade do contador . Da mesma forma, se tentarmos acessar i que irá resultar em um erro como nós não declaramos i no ambiente global." (2015, https://en.wikipedia.org/wiki/Immediately-invoked_function_expression).

Todos esses tópicos abordados aqui fazem parte do ciclo de vida de qualquer programador que use não só JavaScript mas também outras linguagens. É muito importante conhecermos como funciona a linguagem em que programamos para que não haja erros em nossos projetos. As vezes nos preocupamos excessivamente em "o que a linguagem faz" do que "como ela faz" e entender essa segunda parte é essencial para dominar completamente a linguagem escolhida e construir projetos sólidos do inicio ao fim.


##Bibliografia

https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Guide/Closures  
http://loopinfinito.com.br/2014/10/29/hoisting-e-escopo-em-javascript/  
https://msdn.microsoft.com/pt-br/library/bzt2dkta%28v=vs.94%29.aspx  
http://www.w3schools.com/js/js_function_invocation.asp  



