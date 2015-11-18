# Artigo
**autor**: Dânio Filho

### Variáveis em Javascript

Este artigo aborda de maneira geral o funcionamento da criação de variáveis em Javascript, explicando algumas com exemplo alguns recursos que a linguagem tem a oferecer


## Hoisting

Contextualizando, no Javascript é possível atribuir um valor a uma variável e só instancia-la depois.

Exemplo:
```
x = 5;

elem = document.getElementById("demo");
elem.innerHTML = x;                     

var x;

```

O Exemplo acima apenas atribui um valor a variável x e diz que o elemento "demo" receberá seu valor. Ao final, instancia a variável x.

O Javascript reescreve este código da seguinte forma para o executar:

```
var x;
x = 5;

elem = document.getElementById("demo");
elem.innerHTML = x;                     

```

O termo **Hosting** vem de um termo em inglês que significa "levantar" ou "suspender algo", que é justamente o que acontece quando uma variável é instanciada após seu uso, ou seja, ela vai para o topo do escopo e o código passa a reconhecê-la como variável para uso. Em outras palavras, neste processo ocorre o **Hosting** da variável.

Note que apenas uma variável que foi instaciada é que vai para o topo, este processo não acontece quando uma variável é **inicializada**.

Exemplo:

```
var x;
console.log(x);
x = 10;
```

No exemplo acima o código irá gerar um retorno ```undefined``` ao executar porque a variável ```x``` foi **inicializada** apenas depois do comando ```console.log(x)```. Logo torna-se necessário inicializar as variáveis antes da sua execução.

**Hosting em funções**

Este mesmo comportamento acontece com funções também, porém com a ligeira diferença de que todo o seu contexto é *hoisted* também.

Exemplo:

```
lorem();
function lorem(){
   console.log('ipsum')
}
```

Neste exemplo, mesmo que a função ```lorem()``` tenha sido criada depois da sua chamada, o Javascript entendeu pois fez o *Hosting* da função e transformou o código no seguinte:

```
function lorem(){
   console.log('ipsum')
}
lorem();
```

O **Hosting** também ocorre em casos em que a função seja criada mais do que uma vez.

Exemplo:

```
function lorem(){
   function ipsum(){
      return 'dolor';
   }
   return ipsum();
   function ipsum(){
      return 'sit';
   }
}
console.log( lorem() );
```
A função acima da a impressão de que o retorno seria ```"dolor"``` já que o retorno de ```ipsum()``` é definido antes da sua execução. Porém o Javascipt fez o Hosting da função ```ipsum()``` e a colocou atrás da linha ```return ipsum();``` transformando o código para o exemplo abaixo:

```
function lorem(){
   function ipsum(){
      return 'dolor';
   }
   function ipsum(){
      return 'sit';
   }
   return ipsum();
}
console.log( lorem() );
```

Logo o retorno desse código é ```"sit"```

## Closure

Closures são funções criadas dentro de outras funções que possuem acesso às variáveis da função exterior.

Exemplo de **closure**:

```
function soma(x, y){

   var retorno = "O resultado é ";

   function do_soma(){
      returno x + y;
   }

   return do_soma();

}
soma(2+2); // O resultado é 4

```

Note que a função ```do_soma()``` conseguiu acessar as variáveis ```x``` e ```y``` que são da função ```soma()```.

Uma **closure** possui acesso a 3 tipos de escopos: variáveis globais, variáveis definidas dentro da função exterior e seu próprio escopo de variáveis.

As **closures** em Javascript são comumente usadas para emular métodos privados dentro de uma função, ou seja, criar métodos que só podem ser chamados dentro da função externa em que foram criados. Um conceito muito comum no uso de [Classes](https://pt.wikipedia.org/wiki/Classe_(programa%C3%A7%C3%A3o)).


## Variável Global

Variáveis globais em Javascript são variáveis que podem ser usadas por todas as funções que virão na sequência de sua instanciação ou em qualquer lugar do escopo, sendo dentro ou fora de qualquer outra função.

Exemplo:

```
var x;
x = 10;

function getX(){
   return x;
}

console.log( getX() )
```

A variável x foi definida no topo do escopo, ou seja, é uma variável global e pôde ser acessada dentro da função ```getX()``` sem problemas.

O melhor uso para variáveis globais é quando um uma mesma variável precisa ser acessada e modificada por funções.

Um exemplo seria no caso de um jogo onde um jogador possui uma variável que armazena sua quantidade de pontos de vida.

Neste mesmo código podemos ter funções que adicionam e removem pontos de vida do jogador.

```
var pv = 100;

function addPv( valor ){
   pv = pv + valor;
}

function remPv( valor ){
   pv = pv - valor;
}
```

Aqui é possível ter duas funções que trabalham com a mesma variável e conseguem atualiza-la sem problemas.


## Variável por parâmetro

Variáveis definidas via parâmetro são variáveis que são criadas e inicializadas no momento de execução de uma função e são acessíveis apenas através de um escopo local, ou seja, outras funções não possuem acesso ao conteúdo daquela variável e nem ao menos "sabem" que ela existe.

Exemplo:

```
function teste(a){
   return a;
}

console.log(teste(10)); // 10
console.log(a); // Uncaught ReferenceError: a is not defined
```

O exemplo acima retorna 10 no primeiro ```console()``` pois ele invoca a função ```teste(a)``` e passa o parâmetro pra ela. Esta linha não sabe da existencia da variável ```a``` mas mesmo assim consegue acessar seu conteúdo indiretamente pois a função ```teste(a)``` a acessa por ela. Já o segundo ```console()``` retorna um erro dizendo que a variável ```a``` não foi definida pois ela foi definida apenas dentro da função ```teste(a)``` e as demais funções de fora não possuem acesso a ela.

E o que ocorre quando uma variável global possui o mesmo nome de uma que é passada por parâmetro? A resposta é: nada. A variável global não é modificada, mas uma cópia dela é criada e usada dentro da função.

O mesmo exemplo acima, mas criando ```a``` como variável global também:

```
var a = 20;
function teste(a){
   return a;
}

console.log(teste(10)); // 10
console.log(a); // 20
```

A variável ```a``` foi usada dentro da função teste, mas é considerada como outra variável, seu conteúdo é diferente da variável ```a``` definida globalmente.


## Instanciação usando uma IIFE

**IIFE** significa *Immediately-Invoked Function Expression*, ou seja, é uma função que é executada imediatamente logo após ela ser definida.

Um exemplo simples dessa função:

```
(function () {
  console.log('Sou uma IIFE');
})()
```

O conteúdo entre  ```(function() { ... })``` é a função e o ```()``` logo após a função é o comando que chama o retorno dessa função criada.

Para programadores que já usaram jQuery(https://jquery.com/) esta é uma prática muito comum, pois o jQuery utiliza bastante isso.

Esta prática é muito útil para criar variáveis sem interferir com outras variáveis já criadas ou definidas anteriormente em um escopo global. Seu uso mais comum é na criação de bibliotecas.

Vamos a um exemplo:

Em um caso onde temos dois scripts distintos que tratam dos pontos de vida de um personagem e de um monstro:

```
//personagem
var pv = 100;

function addPv( valor ){
   pv = pv + valor;
}

function remPv( valor ){
   pv = pv - valor;
}

//monstro
var pv = 250;

function addPvMonstro( valor ){
   pv = pv + valor;
}

function remPvMonstro( valor ){
   pv = pv - valor;
}

```

Este código iria gerar um conflito pois ambos utilizam a mesma variável com o nome ```pv```. Note que isto é algo muito comum de acontecer em um ambiente em que um programador usa bibliotecas diferentes, pois é extremamente possível que ambas as bibliotecas utilizem variáveis com o mesmo nome.

Resolvendo este problema com IIFE:

```
//personagem
(function(){
   var pv = 100;

   function addPv( valor ){
      pv = pv + valor;
   }

   function remPv( valor ){
      pv = pv - valor;
   }
})()

(function(){
   //monstro
   var pv = 250;

   function addPvMonstro( valor ){
      pv = pv + valor;
   }

   function remPvMonstro( valor ){
      pv = pv - valor;
   }
})()

```

Assim como qualquer função, também é possível passar uma variável como parâmetro para uma **IIFE**. Estas variáváveis passadas serão tratadas como variáveis de escopo daquela função e apenas serão acessíveis dentro dela, o que permite a prática do **IIFE** para utilizar variáveis em um script sem que interfira com outros.

Exemplo:

```
var x  = 100;
(function(x){
console.log(x);
})()
```
Uma **IIFE** também pode ser criada e passada para dentro de uma variável, assim é possível invocar uma função de dentro desta IIFE em qualquer momento que for necessário:

```
var log = (function(){
console.log("Lorem Ipsum");
})()
// blablabla...
log;
```

Outra coisa que é possível fazer é encapsular funções e criar uma espécie de classe utilizando variáveis e IIFE:

```
var  calc = (function(){
	return {
		soma: function(a,b) {
			return a + b;
		}
		sub: function(a,b){
			return a - b;
		}
	}
})()
console.log( calc.soma(10, 20) );
console.log( calc.soma(30, 10) );
```

Note que agora é possível utilizar a variável ```calc``` como uma espécie de classe e usar suas funções a qualquer momento.


## Considerações

Existem momentos em que uma técnica torna-se necessária para resolução de um problema, porém, sem o correto entendimento da linguagem, "gambiarras" serão feitas e isso muitas vezes prejudica o código tanto visualmente como em performance, logo entender como as variáveis são instanciadas no Javascript é muito importante para um programador pois só assim ele saberá exatamente quais ferramentas e recursos a linguagem oferece e só assim ele conseguirá escrever um bom código.
