# Artigo
**autor**: ravenNNN - Baltazar Parra

## Hoisting

Em JavaScript antes do nosso código ser executado, ele é lido por inteiro. Nessa hora, todas nossas variáveis e funções,
são içadas até o topo do nosso escopo, só então a execução de fato acontece. Isso é o que chamamos de Hoisting.

Explicando melhor:

Sempre que criamos uma variável, ela é içada para o topo do nosso escopo, antes mesmo do nosso código ser executado, ou seja,
ela não chega a receber nenhum valor nessa fase, permanecendo indefinida.

```
    valor = 666;
    var valor;

    // Como nossas variáveis são içadas antes da execução do código
    // Ela será interpretada assim

    var valor; // undefined
    valor = 666;

```

Já com as declarações de funções, é um pouco diferente, não é somente o nome que é içado, neste caso todo corpo de nossa função
é levado para o topo do nosso escopo.

```
    coisada(); // vai printar "mensagem coisada"
               // Porque ali em baixo eu vou criar a função

    function coisada() {
      console.log("mensagem coisada");
    }

    // Como nas funções, são içadas o corpo e não somente o nome
    // Eu posso chamar ela em qualquer lugar do código
    // Mesmo não fazendo nenhum sentido aparente.

```
Obs. No caso das expressões, ela vai se comportar como as variáveis, tendo somente seu nome içado.

## Closure

O que é?

Porquê acontece e como usar?

Situações que você usaria:

## Variável Global

Como se usa uma variável Global dentro de uma função?

## Variável por parâmetro

O que acontece dentro da função quando um parâmetro é passado?

## Instanciação usando uma IIFE

Como uma variável pode receber um valor de uma IIFE?

Como passar uma variável por parâmetro para a IIFE? O que acontece com ela dentro da função?
