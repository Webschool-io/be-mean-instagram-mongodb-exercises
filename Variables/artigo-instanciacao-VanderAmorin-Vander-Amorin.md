# Instanciação de variáveis
**autor**: Vander Amorin

Fala galera! Neste artigo iremos ver um pouco sobre instanciação de variáveis em JavaScript passando pelos tópicos: Hoisting, Closures, escopo de variáveis em funções e funções IIFE, com exemplos um poquinho diferentes do que estamos acostumados a ver: usando bandas e músicos de rock/metal.

Let's rock!


## Hoisting

Declarações de variáveis são hasteadas no topo da função. Ou seja, ela serão levantadas e declaradas no topo de uma função (quando criada dentro de uma função) ou no topo do escopo global (quando for uma variável global).
Apenas a declaração de uma variável é hasteada ao topo, e não a inicialização ou atribuição de valores.

Consideremos os exemplos:

<pre><code>
function showBand() {console.log("Favourite band: " + band);
    var band = "SOAD";
    console.log("Favourite band: " + band); 
}
showBand();
/* Retorna:
undefined
SOAD
*/
</code></pre>

A primeira impressão retorna 'undefined' pois ao ser chamada pela primeira vez, 'band' é hasteada no topo da função. Ou seja, ela foi automaticamente declarada como uma variável local que foi chamada na primeira vez.

A função acima é executada da seguinte maneira pelo motor javaScript:
<pre> <code>
function showBand() {
    var band; // 'band' foi hasteada no topo da função e está com valor 'undefined' pois ainda não ocorreu a atribuição de seu valor (mais abaixo)

    console.log("Favourite band: " + band); // Favourite band: undefined
    band = 'SOAD'; // Atribuímos o valor 'SOAD' para a variável 
    console.log("Favourite band: " + band); // Favourite band: SOAD
}
</code> </pre>

Declarações de funções sobrescrevem declarações de variáveis quando hasteadas, exceto quando é atribuído um valor à variável:

<pre> <code>
var band;
function band() {
    console.log('Rammstein');
}

// "band" agora é uma função;

var band = "Metallica";

function band() {
    console.log('something');
}
</code> </pre>

'band' continuará sendo uma variável com o valor 'Metallica', pois o fato de ela ter sido inicializada com um valor sobrescreve a declaração da função.
Expressões de função, como a seguinte, não são hasteadas :

<pre> <code>
var band = function() {

    console.log('Rammsten');
}
</code> </pre>

## Closure

Resumidamente, são funções dentro de funções. Elas possuem acesso as suas variáveis locais, às variáveis da função exterior e variáveis do escopo global. É possível também chamar parâmetros da função que a engloba.
Exemplo:

<pre><code>
function showBandMember(member, band) {
    var text = " from the band ";

    function printText() {
        return member + text + band;
    }

    return printText();
}

showBandMember("Daron Malakian", "SOAD"); // Daron Malakian from the band SOAD
</code></pre>

## Variável Global

Todas as variáveis declaradas fora de funções são variávels de escopo global e estão disponíveis por toda a aplicação. No navegador, o escopo global é o objeto 'window', ou o documento por um todo.

Exemplos de declaração de variáveis globais:

<pre><code>
var band = 'Rammstein';
instrument = 'Guitar';
</code></pre>

Como todas as variáveis globais são anexadas ao 'window', nós podemos acessá-las das seguinte formas:

<pre><code>
console.log(window.band); // Rammstein
console.log("instrument" in window);  // true
</code></pre>

Se uma variável for criada dentro de uma função, sem antes ter sido criada com a utilização de 'var', ela será adicionada ao escopo global:

<pre><code>
function yourBand() {
    band = 'SOAD'; // band é de escopo global pois não foi criada utilizando 'var';
    console.log(band);
}

yourBand(band); // SOAD
 // 'band' também está acessível aqui, pois foi adicionada ao escopo global dentro da função;
 </code></pre>

Exemplo de variáveis de escopo global, mesmo que não pareça:

<pre><code>
for(var i = 0; i <= 10; i++) {
    console.log(i); // Exibe 1, 2, 3...10
}

// i é uma variável blogal, e poderá ser utilizada na função abaixo, recebendo o último valor declarado no loop acima:

function size() {
    console.log(i);
}

size(); // 10
</code></pre>

Funções como 'setTimeout' são executadas no escopo global. Sendo assim, considere o exemplo abaixo:

<pre><code>
var boxSize = 100;
var boxMax = 4;
var obj = {
    boxSize: 200,
    boxMax: 2,
    calc: function() {
        setTimeout( function() {
            console.log( this.boxSize * this.boxMax );
        }, 2500);
    }
}

// Sendo que setTimeout é executada no escopo global, o 'this' utilizado dentro dela irá acessar as variáveis 'boxSize' e 'boxMax' de escopo global, não as que foram declaradas em 'obj';

obj.calc(); // 400
</code></pre>

Dica: evitar poluir o escopo global com variáveis desnecessárias. Exemplos:

<pre><code>
// ERRADO
var band, instrument;

function showBand(){
    console.log( band +'Instruments: '+ instruments );
}

//CERTO
function showBand() {
    var name = "Rammstein", instrument = "Guitar";
    console.log( band +'Instruments: '+ instruments );
}</code></pre>

## Variável por parâmetro

Funções podem receber valores para serem utilizados dentro de seu escopo, são os chamados "parâmetros".
Quando uma variável global é passada como parâmetro a uma função, seu valor é concedido a uma variável local.

Vamos aos exemplos:

<pre><code>
var band = "Angra";
function changeBand(new) {
    new = "Megadeth";
    return new;
}

changeBand(band); // Megadeth
console.log(band); // Angra
</code></pre>

<pre><code>
var band = "Angra";

function changeBand(new) {
    band = new;
    return band;
}

changeBand("Megadeth"); // Megadeth - retorna a variável LOCAL da função
console.log(band); // Angra - retorna a variável global
</code></pre>

Observe que o valor da variável global permanece intacto. Para alterá-lo é preciso criarmos uma nova variável, com nome diferente. Observe:

<pre><code>var band = "Angra";
var newBand = "Megadeth";

function changeBand(new) {
    band = new;
    return band;
}

changeBand(newBand); // Megadeth
console.log(band);
</code></pre>


## Instanciação usando uma IIFE

São funções que são executadas no mesmo momento em que são definidas, como o próprio nome já diz: "IIFE - Immediately-Invoked Function Expression", traduzindo: "Expressão de Função Imediatamente Invocada".

Em javaScript toda função, quando invocada, cria um novo contexto de execução. Tudo que é definido dentro não pode ser acessado "de fora", desde variáveis até funções. Ou seja, invocar uma função nos permite criar "privacidade".

O uso de IIFE é recomendado quando precisamos "proteger" nossas variáveis para 
que códigos de terceiros não possam acessá-las e/ou modificá-las, por exemplo.

<pre><code>
(function(song) {

    var music = "Seek and Destroy";
    console.log(music);

} ("Master of Puppetz") ); // Retorna Master of Puppetz

console.log(music); // music is not defined
</code></pre>

## Referências

http://javascriptbrasil.com/2013/10/11/escopo-de-variavel-e-hoisting-no-javascript-explicado/

http://javascriptbrasil.com/2013/10/12/entenda-closures-no-javascript-com-facilidade/

https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Statements/var