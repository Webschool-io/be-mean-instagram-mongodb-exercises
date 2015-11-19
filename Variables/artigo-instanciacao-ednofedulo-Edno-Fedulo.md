# Artigo
**Autor**: Edno Fedulo

## Hoisting

Hoisting é um comportamento do javascript que move a declaração da variavel para o topo do escopo em que ela se encontra. Isso é possível porque as declarações são processadas antes do código ser executado de fato, possibilitando que uma variável seja utilizada antes de ser declarada.

Exemplo:
```
function findPokemon(name){
    query = "{name: /"+name+"/i}";

    var result = db.pokemons.find(query);

    var query;
}
```

## Closure

Explicando de forma enxuta, closure é uma função dentro de outra função. 
Esta closure tem acesso às variáveis da função em que esta contida. 
Um comportamento interessante das closures é que elas armazenam a referência das variaveis, e não o valor absoluto delas.
Outra característica é que as closures podem ser executadas mesmo que a função em que elas estão contidas já tenha sido encerradas. Isso é possível porque no javascript as closures armazenam o escopo em que foram definidas e armazenam a referência das variaveis, como dito acima.

Exemplo:
```
function pokemon(){
    var pokeName = "Pikachu";

    return {   
        setName: function(newName){
            pokeName = newName;
        },
        getName: function(){
            return pokeName;    
        }
    }
}

var closure = pokemon();
closure.getName(); //Pikachu
closure.setName("Charmander");
closure.getName(); //Charmander
```

## Variável Global

Uma variável global é uma variavel que é declarada fora do escopo de qualquer função, sendo ela acessível por todas as funções, seja ela comuns ou closures.

Exemplo:
```
var pokemonName = "Pikachu";

function teste(){
    console.log(pokemonName); //Pikachu
    var pokemonName = "Charmander";
}

teste(); //Pikachu
```

## Variável por parâmetro

As funções no javascript podem ter N parametros. 
Caso a função seja chamada sem que todos os parametros sejam passados, os parametros faltantes serão setados como undefined.
A função recebe os parametros por valor, e não por referência. Sendo assim, caso uma variável global seja passado para uma função, apenas o valor dela no momento da execução é que será recebido pela função. Desta mesma forma, caso o valor recebido na função seja alterado, isso não altera o valor da variavel global.

Exemplo:
```
var x = 20;

function teste(number){
    number = number + 10;
    console.log(number);
}

teste(x); // 30
console.log(x); // 20
```
	

## Instanciação usando uma IIFE

Uma IIFE é uma função que é executada no momento em que é definida. É muito útil quando queremos tornar de certa forma privados as variaveis utilizadas na função em questão, evitando que codigos alheios alterem o valor das mesmas.

Quando se refere a retorno de valores e ao recebimento de parametros, uma IIFE se comporta igualmente a uma função comum, mudando apenas a forma como é declarada, sendo que estes parametros devem ser passados no () externo a função que caracteriza a IIFE em si.

Exemplo:
```
var fn = (function () { 
            return 10; 
        }())
fn; //10 é o retorno da IIFE

(function (string) {
    console.log(string)
}('Pikachu')) //Pikachu é passado por parâmetro 
```
