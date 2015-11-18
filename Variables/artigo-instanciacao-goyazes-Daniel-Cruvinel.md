# Instanciação com Javascript
autor: Daniel Cruvinel

## Hoisting

Hoisting é a característica de o interpretador JavaScript mover as variáveis declarativas e funções declarativas para o topo de seus escopos atuais.
Todas as variáveis declarativas são movidas para o topo da função, se definida dentro da função, ou para o topo do contexto global, se fora da função.

    ```
        function TaxonomiaDoGato() {
            console.log(“Gato Reino: ” +  reino);
            var reino = “Animalia”;
            console.log(“Reino do Gato:  ” + reino);
        }
        TaxonomiaDoGato();
        // Gato Reino: undefined
        // Reino do Gato: Animalia
        // Gato Reino retorna undefined, porque a variável local foi movida para o topo da função, ou seja essa variável local é chamada primeiro.
        
        //exemplo de como o código é processado no interpretador JavaScript

        function TaxonomiaDoGato(){
            var reino; // reino foi movida para o topo da função, perceba que a atribuição só será feita abaixo.
            console.log(“Gato Reino: “ + reino); // Gato Reino: undefined
            reino = “Animalia”; // agora é atribuído um valor ao reino
            console.log(“Reino do Gato: “ + reino); // Reino do Gato: Animalia
        }
    ```

Apenas as funções declarativas e variáveis declarativas que são movidas para o topo do seu escopo atual. Funções declarativas têm prioridade sobre as variáveis declarativas.

## Closure
A variável do JavaScript pode pertencer à variável local ou  variável global. Variáveis privadas são possíveis com closures.
Uma closure é uma função interna que tem acesso as variáveis da função que a envolve. 

A closure possui três cadeia de escopo:

a closure tem acesso ao seu próprio escopo(variáveis definidas dentro de suas chaves {} ); 
tem acesso as variáveis da função que a envolve; 
e tem acesso as variáveis globais.

Você cria uma closure adicionando uma função dentro de outra função
Exemplo:

    ```
        function TaxonomiaDoGato(reino, especie) {
            var animal = "Gato";
            function taxonomia() {
                return animal + " " + "Reino: " + reino + "," + " Especie: " + especie;
            }
            return taxonomia();
        }

        TaxonomiaDoGato("Animalia", "felis silvestris cactus"); // Gato Reino: Animalia, Especie: felis silvestris cactus
    ```

## Variável Global
A variável declarada fora de uma função se torna global.
Uma variável global tem escopo global. Todo o script e funções tem acesso a ela.
Exemplo:

    ```
        var felinoNome =  "Tigre";
        // todo o código aqui pode usar felinoNome

        function minhaFuncao() {
            // todo código aqui pode usar felinoNome
        }
    ```

Se o valor da variável global for alterado dentro da função, também será alterado o valor da variável global fora da função.
Exemplo:

    ```
        var felinoNome =  "Tigre";
        // todo o código aqui pode usar felinoNome

        function minhaFuncao() {
            // todo código aqui pode usar felinoNome
            felinoNome = "Jaguatirica";
            console.log(felinoNome);
        }

        minhaFuncao(); // Jaguatirica
        console.log(felinoNome);  // Jaguatirica, a alteração feita dentro da função alterou o valor da variável fora da função.
    ```

## Variável por Parâmetro
No javascript, uma função é um objeto, portanto ela pode ser passada como parâmetro com a mesma sintaxe de uma variável.

    ```
        function MiadoDoGato() {
            return console.log('Miauu!');
        }

        function Gato(parametro) {
            parametro.call(); // executa parâmetro
        }

        Gato(MiadoDoGato); // Miauu!
    ```

## Instanciação usando uma IIFE
IIFE - Immediately Invoked Function Expression, é uma função, imediatamente, executada após ser criada. Ao criar uma função anônima com execução imediata, podemos criar um escopo temporário para nossas funções e variáveis.

A sintaxe da IIFE é você transformar a função em Function Expression e, no final adicionar parênteses (), esses mesmos parênteses se tornam uma invocação de uma função.

Sintaxe: (...)();

Exemplo:

    ```
        (function fazAlgumaCoisa() { /* codigo */ })();
    ```

Ou como função anônima:

    ```
        (function() { /* codigo */ })();
    ```

Dentro dos parênteses finais você pode utilizar parâmetros.
Exemplo:

    ```
        (function gato(mia) { console.log(mia); })('Miau!'); // Miau!
    ```


## Referência

http://javascriptissexy.com/javascript-variable-scope-and-hoisting-explained/
http://www.w3schools.com/js/js_scope.asp
http://gregfranko.com/blog/i-love-my-iife/
http://imasters.com.br/front-end/javascript/sobre-funcoes-imediatas-javascript-iife/


