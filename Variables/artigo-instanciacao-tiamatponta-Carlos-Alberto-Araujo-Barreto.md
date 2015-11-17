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



Explique o que é, o porquê acontece e como acontece com variável e função.

## Closure

Explique o que é, o porquê acontece e como usar. 
Cite situações que você usaria.

## Variável Global

Explique como se usa uma var Global dentro de uma função.

## Variável por parâmetro

Explique o que acontece dentro da função qnd um parâmetro é passado e também explique quando uma GLOBAL é passada por parâmetro.


## Instanciação usando uma IIFE

Explique como uma variável pode receber um valor de uma IIFE.
Explique como passar uma variável por parâmetro para a IIFE e acontece com ela dentro da função.



