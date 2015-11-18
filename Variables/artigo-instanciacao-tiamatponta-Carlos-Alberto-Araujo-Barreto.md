# Artigo
**autor**: Carlos Alberto Araujo Barreto

## Hoisting
Hoisting é o comportamento padrão do Javascript de mover declarações de variáveis para o topo.
Em javascript uma variável pode ser usada antes de ter sido declarada.
Exemplo:
```
var x = 1; // Inicializa x

Elemento = document.getElementById("teste"); // Encontra um elemento
Elemento.innerHTML = x + " " + y; // Exibe x e y

var y = 7; // Inicializa y
```
No exemplo anterior o valor de x é exibido, e y é exibido como undefined, pois apesar de existir a declaração var y, o valor é
usado antes de declaração.
Se ao invés de "var y = 7;" fosse usado somente "y = 7" não haveria resultados pois teríamos um bug.

Hoisting é basicamente isso, as declarações das variáveis mesmo ao longo do código são mantidas como se 
estivessem sendo declaradas no topo, mas por recomendação é melhor manter as declarações de variáveis no topo do código.


## Closure

Closure são funções que se referem a variáveis livres(https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Guide/Closures).
De maneira mais simples uma closure é uma função tendo acesso ao escopo de uma função parente, mesmo
após esta função já ter sido fechada.
Exemplo 1:
```
var adicionar = (function () {
    var cont = 0;
    return function () {return cont += 1;}
})();

adicionar();
adicionar();
adicionar();
// o contador agora tem valor 3
```
Exemplo 2:
```
function start() {
  var nome = "Carlos";
  function ExibeNome() {
    alert(nome);
  }
  ExibeNome();
}
start();
```
Nos exemplos 1 e 2 temos o comportamento de closures através tanto de funções como de variáveis.


## Variável Global

Variável global é uma variável que é visível a todo o escopo da aplicação.
Sua utilização mais comum é para contadores, variáveis que armazenam dados de navegação
do usuário para efeito de controle, variáveis que sejam necessárias serem acessadas de dentro das funções.

Exemplo:
```
var n = "Alô pokemons";

function digaAlo()
{
  alert(n);
}
```
Nesta função acessamos a variável global n que está fora da função digaAlo() e exibimos em um alerta do navegador.

## Variável por parâmetro

Quando uma variável é passada por parâmetro é criada uma instância local daquela variável dentro da função,
e toda modificação que esta variável sofrer internamente à função fica limitada ao escopo da função, quando retornar
para a chamada da função o parametro terá o mesmo valor antes de chamar a função.
Exemplo:
```
function soma(n1, n2)
{
  n1 += n2;
  alert(n1);
}

n1 = 2;
n2 = 3;

soma(n1, n2); // Exibe o valor 5
alert(n1); // Exibe o valor 2

```

Quando uma variável global é passada por parâmetro ela é referenciada localmente à função passada,
e assim como as demais variáveis toda alteração que ela sofrer internamente só acontecerá no escopo local da função,
ao retornar à chamada da função ela manterá seu valor anterior.
Exemplo:
```
x = 5;
function add(y) 
{
  y++;
  return y;
}
alert(add(x)); // Exibe o valor 6
alert(x); // Exibe o valor 5
```

## Instanciação usando uma IIFE

O termo IIFE significa "Immediately Invoked Function Expression", que representa uma função que é executada sem necessidade de uma chamada para ela.
Um exemplo de atribuição de uma IIFE para uma variável será demonstrado a seguir:
```
var iife = (function() {return 1});
var iife2 = (function() {return 2}()); // Outra maneira de declarar a IIFE
alert(iife); // Exibe o valor 1
alert(iife2); // Exibe o valor 2
```

Quando trabalhamos com parametros algumas mudanças devem acontecer.
No exemplo anterior vimos uma segunda forma de declarar uma IIFE, com um "()" antes de fechar o primeiro parênteses aberto.
Nesse "()" podemos passar parâmetros para a função, que assimo como nos demais casos
os parâmetros passados serão tratados em escopo local à função, como será visto no exemplo a seguir:
```
(function(string)
{
  alert(string)
}('Alô mundo'));
```


