# MongoDB - Aula 04 - Exercício
autor: Daniel Cruvinel

## 1. Adicionar 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.

    ```
    var pikachu = {name: /pikachu/i}
    var mod = {$pushAll: {ataque: ['choque do trovao', 'choque']}}
    db.pokemons.update(pikachu, mod)

    var squirtle = {name: /squirtle/i}
    var mod = {$pushAll: {ataque: ['agua ataque', 'molhar']}}
    db.pokemons.update(squirtle, mod)

    var bulbassauro = {name: /bulbassauro/i}
    var mod = {$pushAll: {ataque: ['bulba', 'saurofínite']}}
    db.pokemons.update(bulbassauro, mod)

    var charmander = {name: /charmander/i}
    var mod = {$pushAll: {ataque: ['fofuras', 'doublefofuras']}}
    db.pokemons.update(charmander, mod)



    ```

## 2. Adicionar 1 movimento em todos os pokemons: 'desvio'.

    ```
    var query = {}
    var mod = {
        $push: {moves: desvio}   
    }
    var options = {multi: true}
    db.pokemons.update(query,mod, options)

    ```

## 3.Adicionar o pokemon 'AindaNaoExisteMon' caso ele não exista com todos os dados com o valor 'null' e a descrição: "Sem maiores informações."

    ```
    var query = {name: /AindaNaoExisteMon/i}
    var mod = {
        $setOnInsert: {name: "AindaNaoExisteMon", ataque: null, movimento: null, description: "Sem maiores informações"}
    }
    var options = {upsert: true}
    db.pokemons.update(query, mod, options)

    ```

## 4. Pesquisar todos os pokemons que possuam o ataque 'investida' e mais um que você adicionou, escolha seu pokemon favorito.

    ```
    var query = {ataque: {$in: [/investida/i, /fofura/i ]}
    db.pokemons.find(query)

    ```

## 5. Pesquisar todos os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.

    ```
    var query = {moves: {$all: [/investida/i, /fofura/i}}
    db.pokemons.find(query)
    ```

## 6. Pesquisar todos que não são do tipo 'elétrico'.

    ```
    var query = {tipo: {$ne: 'eletrico'} }
    db.pokemons.find(query)

    ```

## 7. Pesquisar todos pokemons que tenham o ataque 'investida' e tenham a defesa não menor ou igual a 49.

    ```
    var query = {$and: [{moves: {$in: ['investida']}}, {attack: {$not: {$lte: 49}}}]}
    db.pokemons.find(query)

    ```

## 8. Remova todos os pokemons do tipo água e com attack menor que 50

    ```
    query = {$and: [ {type: /água/i}, {attack: {$lt: 50}}]}
    db.pokemons.remove(query)
    ```

## 9. Demonstre qual a diferença entre os operadores $ne e $not

    ```
    $ne não pode usar regex, enquanto $not é permitido o uso.
    O operador $not só afeta outros operadores e não pode checar campos e documentos independentemente. Use $not para disjunções lógicas e $ne para testar o conteúdo do campo diretamente.
    Ex. :
    > db.pokemons.find(query).pretty()
    {
        "_id" : ObjectId("57094b59c6fbfba57cc8c71e"),
        "active" : true,
        "name" : "NaoExisteMon",
        "attack" : null,
        "defense" : null,
        "height" : null,
        "description" : "sem maiores infor",
        "ataque" : [
                "choque do trovao",
                "choque"
        ]
    }
    > var ataque = {attack: {$ne: /null/i }}
    > db.pokemons.find(ataque)
    Error: error: {
        "$err" : "Can't canonicalize query: BadValue Can't have regex as arg to $ne.",
        "code" : 17287
    }

    Ao tentar usar regex o mongodb retorna a mensagem de erro informando que não pode ter regex como argumento de $ne.
    ```