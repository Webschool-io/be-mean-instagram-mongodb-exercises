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

Já com as declarações de funções é um pouco diferente, não é somente o nome que é içado, neste caso todo corpo da nossa declaração é levado para o topo.

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

Antes de falar sobre as closures, você precisar entender o escopo das variáveis.
O escopo nada mais é que, o ambiente onde você declarou sua variável,
esse ambiente demarca o limite onde você pode usar sua variável.

Simplificando, closure é uma função interna, que te permite acessar variáveis externas.

```
    function zeRuela (nomeDoRuela, sobrenomeDoRuela) {
        var chamada = "Eu sou o ";
        
    // Função externa, com variáveis externas.    
    
        function nomeInteiro () {
            return chamada + nomeDoRuela + " " + sobrenomeDoRuela;
        }
            return nomeInteiro ();
            }

    // Função interna, que tem acesso as variáveis da função externa.
    // Isso é oque chamamos de closure, Ela pode acessar tanto as variáveis,
    // quanto os paramêtros do lado de fora.
    
    
    zeRuela ("Jose", "Arruelo"); // Eu sou o Jose Arruelo
```

Ai em cima temos uma função dentro de outra função, onde a função que está dentro, tem acessos a dados da função de está fora, isso é oque podemos chamar de closure.

## Variável Global

Como se usa uma variável Global dentro de uma função?

## Variável por parâmetro

O que acontece dentro da função quando um parâmetro é passado?

## Instanciação usando uma IIFE

Como uma variável pode receber um valor de uma IIFE?

Como passar uma variável por parâmetro para a IIFE? O que acontece com ela dentro da função?
