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

Ai em cima temos uma função dentro de outra função, onde a função que está dentro, tem acessos a dados da função que está fora, isso é oque podemos chamar de closure.

- Beleza, e eu uso isso pra'quê?

Para construir variáveis privadas ué.

Uma função pode acessar todas variáveis criadas dentro dela, e com as closures podemos acessar também variáveis criadas do lado de fora,
sem bagunçar nosso escopo global deixando nosso código mais inteligivel.

## Variável Global

Para chamar uma variável global dentro de uma função, obviamente declaramos ela em escopo global, e depois chamamos ela dentro da nossa função.

```
var global = 3;

function chamada() {
  return global * 2;
}

chamada(); // 6
```

## Variável por parâmetro

Passando nosso parâmetro por meio de uma variável, ela vai ficar responsável em fazer o transporte do nosso argumento.

```
    var valor = 5;

    function pegaValor(parametro) {
        alert(parametro);
    }

    pegaValor(valor); // 5

    // Passamos uma variavel como parametro

    valor = 12;

    pegaValor(valor); // 12

    // Mudando o argumento da função.
```

Criamos uma variável com o valor 5 e chamamos nossa função passando esta variável como parâmetro, depois alteramos nosso argumento trocando o valor da nossa variável.

## Instanciação usando uma IIFE

Até o ano de 2010, davamos o nome de self-executing anonymous function, para funções executadas no momento em que eram definidas.

```
    (function () {
        console.log('E ae, meu nome é Self-Executing Anonynous Function, Prazer')
    }())
```

Até que um cara chamado Cowboy (Ben Alman) publicou um [longo artigo](http://benalman.com/news/2010/11/immediately-invoked-function-expression/) sobre como não concordava com esse nome,
cunhando o termo IIFE.

(Artigo em Desenvolvimento...)
