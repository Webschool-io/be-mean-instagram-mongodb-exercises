# MongoDB - Aula 04 - Exercício
autor: ANDERSON DA LUZ MORAES

## 1. Adicionar 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.

    ```
    Anderson-iMac(mongod-3.0.5) be-mean-pokemons> var query = {name: {$in: [/pikachu/i, /squirtle/i, /bulbassauro/i, /charmander/i]}}
    Anderson-iMac(mongod-3.0.5) be-mean-pokemons> var mod = { $pushAll: { moves: ['Jato Congelante', 'Salto para trás'] }}
    Anderson-iMac(mongod-3.0.5) be-mean-pokemons> var options = { multi: true }

    Anderson-iMac(mongod-3.0.5) be-mean-pokemons> db.pokemons.update(query, mod, options)
    Updated 4 existing record(s) in 15ms
    WriteResult({
      "nMatched": 4,
      "nUpserted": 0,
      "nModified": 4
    })

    Anderson-iMac(mongod-3.0.5) be-mean-pokemons> db.pokemons.find(query)
    {
      "_id": ObjectId("5644a3cdc21cb248fe6e99fc"),
      "name": "Bulbassauro",
      "description": "Chicote de trepadeira",
      "type": "grama",
      "attack": 49,
      "height": 0.4,
      "active": false,
      "moves": [
        "investida",
        "folha navalha",
        "Jato Congelante",
        "Salto para trás"
      ]
    }
    {
      "_id": ObjectId("5644a37cc21cb248fe6e99fb"),
      "name": "Pikachu",
      "description": "Rato elétrico bem fofinho",
      "type": "electric",
      "attack": 55,
      "height": 0.4,
      "active": false,
      "moves": [
        "investida",
        "choque do trovão",
        "Jato Congelante",
        "Salto para trás"
      ]
    }
    {
      "_id": ObjectId("5644a3cdc21cb248fe6e99fd"),
      "name": "Charmander",
      "description": "Esse é o cão chupando manga de fofinho",
      "type": "fogo",
      "attack": 52,
      "height": 0.6,
      "active": false,
      "moves": [
        "investida",
        "lança-chamas",
        "Jato Congelante",
        "Salto para trás"
      ]
    }
    {
      "_id": ObjectId("5644a3cdc21cb248fe6e99fe"),
      "name": "Squirtle",
      "description": "Ejeta água que passarinho não bebe",
      "type": "água",
      "attack": 48,
      "height": 0.5,
      "active": false,
      "moves": [
        "investida",
        "hidro bomba",
        "Jato Congelante",
        "Salto para trás"
      ]
    }
    Fetched 4 record(s) in 4ms

    ```

## 2. Adicionar 1 movimento em todos os pokemons: desvio.

    ```
    Anderson-iMac(mongod-3.0.5) be-mean-pokemons> var query = {}
    Anderson-iMac(mongod-3.0.5) be-mean-pokemons> var mod = {$push: {moves: 'Desvio'}}
    Anderson-iMac(mongod-3.0.5) be-mean-pokemons> var options = {multi: true}
    Anderson-iMac(mongod-3.0.5) be-mean-pokemons> db.pokemons.update(query, mod, options)
    Updated 11 existing record(s) in 1ms
    WriteResult({
      "nMatched": 11,
      "nUpserted": 0,
      "nModified": 11
    })

    ```


## 3. Adicionar o pokemon AindaNaoExisteMon caso ele não exista com todos os dados com o valor null e a descrição: "Sem maiores informações".

    ```
    Anderson-iMac(mongod-3.0.5) be-mean-pokemons> var query = {name: /AindaNaoExisteMon/i}
    Anderson-iMac(mongod-3.0.5) be-mean-pokemons> var mod = {
      "$set": {
        "description": "Sem maiores informações"
      },
      "$setOnInsert": {
        "name": "AindaNaoExisteMon",
        "attack": null,
        "defense": null,
        "height": null,
        "active": null
      }
    }
    Anderson-iMac(mongod-3.0.5) be-mean-pokemons> var options = { upsert: true }

    Anderson-iMac(mongod-3.0.5) be-mean-pokemons> db.pokemons.update(query, mod, options)
    Updated 1 new record(s) in 2ms
    WriteResult({
      "nMatched": 0,
      "nUpserted": 1,
      "nModified": 0,
      "_id": ObjectId("564dc013cadd5a22756e1408")
    })


    Anderson-iMac(mongod-3.0.5) be-mean-pokemons> var query = {"_id": ObjectId("564dc013cadd5a22756e1408")}
    Anderson-iMac(mongod-3.0.5) be-mean-pokemons> db.pokemons.find(query)
    {
      "_id": ObjectId("564dc013cadd5a22756e1408"),
      "description": "Sem maiores informações",
      "name": "AindaNaoExisteMon",
      "attack": null,
      "defense": null,
      "height": null,
      "active": null
    }
    Fetched 1 record(s) in 0ms

    ```

## 4. Pesquisar todos o pokemons que possuam o ataque investida e mais um que você adicionou, escolha seu pokemon favorito.

    ```
    Anderson-iMac(mongod-3.0.5) be-mean-pokemons> var query = { "moves" : { "$all" : [ "investida", "Jato Congelante" ] } }
    Anderson-iMac(mongod-3.0.5) be-mean-pokemons> db.pokemons.find(query)
    {
      "_id": ObjectId("5644a37cc21cb248fe6e99fb"),
      "name": "Pikachu",
      "description": "Rato elétrico bem fofinho",
      "type": "electric",
      "attack": 55,
      "height": 0.4,
      "active": false,
      "moves": [
        "investida",
        "choque do trovão",
        "Jato Congelante",
        "Salto para trás",
        "Desvio"
      ]
    }
    {
      "_id": ObjectId("5644a3cdc21cb248fe6e99fd"),
      "name": "Charmander",
      "description": "Esse é o cão chupando manga de fofinho",
      "type": "fogo",
      "attack": 52,
      "height": 0.6,
      "active": false,
      "moves": [
        "investida",
        "lança-chamas",
        "Jato Congelante",
        "Salto para trás",
        "Desvio"
      ]
    }
    {
      "_id": ObjectId("5644a3cdc21cb248fe6e99fe"),
      "name": "Squirtle",
      "description": "Ejeta água que passarinho não bebe",
      "type": "água",
      "attack": 48,
      "height": 0.5,
      "active": false,
      "moves": [
        "investida",
        "hidro bomba",
        "Jato Congelante",
        "Salto para trás",
        "Desvio"
      ]
    }
    {
      "_id": ObjectId("5644a3cdc21cb248fe6e99fc"),
      "name": "Bulbassauro",
      "description": "Chicote de trepadeira",
      "type": "grama",
      "attack": 49,
      "height": 0.4,
      "active": false,
      "moves": [
        "investida",
        "folha navalha",
        "Jato Congelante",
        "Salto para trás",
        "Desvio"
      ]
    }
    Fetched 4 record(s) in 1ms

    ```

## 5. Pesquisar todos os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.

    ```
    Anderson-iMac(mongod-3.0.5) be-mean-pokemons> var query = { "moves" : { "$all" : [ "Jato Congelante", "Salto para trás" ] } }
    Anderson-iMac(mongod-3.0.5) be-mean-pokemons> db.pokemons.find(query)
    {
      "_id": ObjectId("5644a37cc21cb248fe6e99fb"),
      "name": "Pikachu",
      "description": "Rato elétrico bem fofinho",
      "type": "electric",
      "attack": 55,
      "height": 0.4,
      "active": false,
      "moves": [
        "investida",
        "choque do trovão",
        "Jato Congelante",
        "Salto para trás",
        "Desvio"
      ]
    }
    {
      "_id": ObjectId("5644a3cdc21cb248fe6e99fd"),
      "name": "Charmander",
      "description": "Esse é o cão chupando manga de fofinho",
      "type": "fogo",
      "attack": 52,
      "height": 0.6,
      "active": false,
      "moves": [
        "investida",
        "lança-chamas",
        "Jato Congelante",
        "Salto para trás",
        "Desvio"
      ]
    }
    {
      "_id": ObjectId("5644a3cdc21cb248fe6e99fe"),
      "name": "Squirtle",
      "description": "Ejeta água que passarinho não bebe",
      "type": "água",
      "attack": 48,
      "height": 0.5,
      "active": false,
      "moves": [
        "investida",
        "hidro bomba",
        "Jato Congelante",
        "Salto para trás",
        "Desvio"
      ]
    }
    {
      "_id": ObjectId("5644a3cdc21cb248fe6e99fc"),
      "name": "Bulbassauro",
      "description": "Chicote de trepadeira",
      "type": "grama",
      "attack": 49,
      "height": 0.4,
      "active": false,
      "moves": [
        "investida",
        "folha navalha",
        "Jato Congelante",
        "Salto para trás",
        "Desvio"
      ]
    }
    Fetched 4 record(s) in 20ms

    ```

## 6. Pesquisar todos os pokemons que não são do tipo eletric.

    ```
    Anderson-iMac(mongod-3.0.5) be-mean-pokemons> var query = {type: {$ne: 'eletric'}}
    Anderson-iMac(mongod-3.0.5) be-mean-pokemons> db.pokemons.find(query)
    {
      "_id": ObjectId("56447efac21cb248fe6e99f5"),
      "name": "Hitmonchan",
      "description": "Espírito de Boxeador",
      "type": "lutador",
      "attack": 50,
      "defense": 30,
      "height": 1.4,
      "active": false,
      "moves": [
        "investida",
        "Desvio"
      ]
    }
    {
      "_id": ObjectId("56447efac21cb248fe6e99f6"),
      "name": "Lickitung",
      "description": "Lambedor",
      "type": "normal",
      "attack": 30,
      "defense": 30,
      "height": 1.2,
      "active": false,
      "moves": [
        "investida",
        "Desvio"
      ]
    }
    {
      "_id": ObjectId("56447efac21cb248fe6e99f7"),
      "name": "Charmeleon",
      "description": "Fogo no rabo",
      "type": "fogo",
      "attack": 30,
      "defense": 30,
      "height": 1.1,
      "active": false,
      "moves": [
        "investida",
        "Desvio"
      ]
    }
    {
      "_id": ObjectId("56447efac21cb248fe6e99f8"),
      "name": "Blastoise",
      "description": "Pokemon da água",
      "type": "água",
      "attack": 40,
      "defense": 40,
      "height": 1.6,
      "active": false,
      "moves": [
        "investida",
        "Desvio"
      ]
    }
    {
      "_id": ObjectId("56447efac21cb248fe6e99f9"),
      "name": "Rattata",
      "description": "Rato roxo",
      "type": "normal",
      "attack": 30,
      "defense": 20,
      "height": 0.3,
      "active": false,
      "moves": [
        "investida",
        "Desvio"
      ]
    }
    {
      "_id": ObjectId("5644a21bc21cb248fe6e99fa"),
      "name": "Gramium",
      "description": "Pokemon da grama",
      "type": "grama",
      "attack": 30,
      "defense": 35,
      "height": 0.4,
      "active": false,
      "moves": [
        "investida",
        "Desvio"
      ]
    }
    {
      "_id": ObjectId("564cf687cadd5a22756e1406"),
      "active": false,
      "moves": [
        "investida",
        "Desvio"
      ]
    }
    {
      "_id": ObjectId("5644a37cc21cb248fe6e99fb"),
      "name": "Pikachu",
      "description": "Rato elétrico bem fofinho",
      "type": "electric",
      "attack": 55,
      "height": 0.4,
      "active": false,
      "moves": [
        "investida",
        "choque do trovão",
        "Jato Congelante",
        "Salto para trás",
        "Desvio"
      ]
    }
    {
      "_id": ObjectId("5644a3cdc21cb248fe6e99fd"),
      "name": "Charmander",
      "description": "Esse é o cão chupando manga de fofinho",
      "type": "fogo",
      "attack": 52,
      "height": 0.6,
      "active": false,
      "moves": [
        "investida",
        "lança-chamas",
        "Jato Congelante",
        "Salto para trás",
        "Desvio"
      ]
    }
    {
      "_id": ObjectId("5644a3cdc21cb248fe6e99fe"),
      "name": "Squirtle",
      "description": "Ejeta água que passarinho não bebe",
      "type": "água",
      "attack": 48,
      "height": 0.5,
      "active": false,
      "moves": [
        "investida",
        "hidro bomba",
        "Jato Congelante",
        "Salto para trás",
        "Desvio"
      ]
    }
    {
      "_id": ObjectId("5644a3cdc21cb248fe6e99fc"),
      "name": "Bulbassauro",
      "description": "Chicote de trepadeira",
      "type": "grama",
      "attack": 49,
      "height": 0.4,
      "active": false,
      "moves": [
        "investida",
        "folha navalha",
        "Jato Congelante",
        "Salto para trás",
        "Desvio"
      ]
    }
    {
      "_id": ObjectId("564dc013cadd5a22756e1408"),
      "description": "Sem maiores informações",
      "name": "AindaNaoExisteMon",
      "attack": null,
      "defense": null,
      "height": null,
      "active": null
    }
    Fetched 12 record(s) in 3ms

    ```



## 7. Pesquisar todos pokemons que tenham o ataque investida E tenham a defesa não menor ou igual a 49.

    ```
    Anderson-iMac(mongod-3.0.5) be-mean-pokemons> var query = {$and: [ { moves: "investida"}, {defense: {$gte: 49}}]}
    Anderson-iMac(mongod-3.0.5) be-mean-pokemons> db.pokemons.find(query)
    Fetched 0 record(s) in 0ms

    ```



## 8. Remova todos os pokemons do tipo água e com attack menor que 50.

    ```
    Anderson-iMac(mongod-3.0.5) be-mean-pokemons> var query = {$and : [{type: 'água'},{attack:{$lt: 50} }] }
    Anderson-iMac(mongod-3.0.5) be-mean-pokemons> db.pokemons.remove(query)
    Removed 2 record(s) in 1ms
    WriteResult({
      "nRemoved": 2
    })

    ```
