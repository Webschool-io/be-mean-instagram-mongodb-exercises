# MongoDB - Aula 04 - Exercício
autor: LEONARDO FILIPE

## **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.
```js
Leonardos-MacBook-Pro(mongod-3.2.0) be-mean-instagram> var query = {name: /pikachu/i}
Leonardos-MacBook-Pro(mongod-3.2.0) be-mean-instagram> var mod = {$pushAll: {moves: ["raio do trovão", "agilidade"]}}
Leonardos-MacBook-Pro(mongod-3.2.0) be-mean-instagram> db.pokemons.update(query, mod)
Updated 1 existing record(s) in 13ms
WriteResult({
    "nMatched": 1,
    "nUpserted": 0,
    "nModified": 1
})
Leonardos-MacBook-Pro(mongod-3.2.0) be-mean-instagram> var query = {name: /squirtle/i}
Leonardos-MacBook-Pro(mongod-3.2.0) be-mean-instagram> var mod = {$pushAll: {moves: ["jato d'água", "chicote de cauda"]}}
Leonardos-MacBook-Pro(mongod-3.2.0) be-mean-instagram> db.pokemons.update(query, mod)
Updated 1 existing record(s) in 6ms
WriteResult({
    "nMatched": 1,
    "nUpserted": 0,
    "nModified": 1
})
Leonardos-MacBook-Pro(mongod-3.2.0) be-mean-instagram> var query = {name: /bulbassauro/i}
Leonardos-MacBook-Pro(mongod-3.2.0) be-mean-instagram> var mod = {$pushAll: {moves: ["folha navalha", "chicote de vinha"]}}
Leonardos-MacBook-Pro(mongod-3.2.0) be-mean-instagram> db.pokemons.update(query, mod)
Updated 1 existing record(s) in 4ms
WriteResult({
    "nMatched": 1,
    "nUpserted": 0,
    "nModified": 1
})
Leonardos-MacBook-Pro(mongod-3.2.0) be-mean-instagram> var query = {name: /charmander/i}
Leonardos-MacBook-Pro(mongod-3.2.0) be-mean-instagram> var mod = {$pushAll: {moves: ["arranhão", "lança chamas"]}}
Leonardos-MacBook-Pro(mongod-3.2.0) be-mean-instagram> db.pokemons.update(query, mod)
Updated 1 existing record(s) in 3ms
WriteResult({
    "nMatched": 1,
    "nUpserted": 0,
    "nModified": 1
})
```


## **Adicionar** 1 movimento em todos os pokemons: `desvio`.##
```js
Leonardos-MacBook-Pro(mongod-3.2.0) be-mean-instagram> var query = {}
Leonardos-MacBook-Pro(mongod-3.2.0) be-mean-instagram> var mod = {$push: {moves: "desvio"}}
Leonardos-MacBook-Pro(mongod-3.2.0) be-mean-instagram> var options = {multi: true}
Leonardos-MacBook-Pro(mongod-3.2.0) be-mean-instagram> db.pokemons.update(query, mod, options)
Updated 5 existing record(s) in 11ms
WriteResult({
    "nMatched": 5,
    "nUpserted": 0,
    "nModified": 5
})
```


## **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".##
```js
Leonardos-MacBook-Pro(mongod-3.2.0) be-mean-instagram> var query = {name: /AindaNaoExisteMon/i}
Leonardos-MacBook-Pro(mongod-3.2.0) be-mean-instagram> var mod = {$setOnInsert: {name: "AindaNaoExisteMon", description: null, type: null, attack: null, defense: null, height: null}}
Leonardos-MacBook-Pro(mongod-3.2.0) be-mean-instagram> var options = {upsert: true}
Leonardos-MacBook-Pro(mongod-3.2.0) be-mean-instagram> db.pokemons.update(query, mod, options)
Updated 1 new record(s) in 11ms
WriteResult({
    "nMatched": 0,
    "nUpserted": 1,
    "nModified": 0,
    "_id": ObjectId("568333b8465179df99fcfdd8")
})
```


## Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.##
```js
Leonardos-MacBook-Pro(mongod-3.2.0) be-mean-instagram> var query = {moves: {$in: [/investida/i, /arranhão/i]}}
Leonardos-MacBook-Pro(mongod-3.2.0) be-mean-instagram> db.pokemons.find(query)
{
    "_id": ObjectId("5670bde8dbd364f21b5949b6"),
    "name": "Charmander",
    "description": "Esse é o cão chupando manga de fofinho",
    "type": "fogo",
    "attack": 52,
    "height": 0.6,
    "moves": [
        "arranhão",
        "lança chamas",
        "desvio"
    ]
}
Fetched 1 record(s) in 1ms
```


## Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.##
```js
Leonardos-MacBook-Pro(mongod-3.2.0) be-mean-instagram> var query = {moves: {$all: [/desvio/i, /folha navalha/i, /chicote de vinha/i]}}
Leonardos-MacBook-Pro(mongod-3.2.0) be-mean-instagram> db.pokemons.find(query)
{
    "_id": ObjectId("5670bde3dbd364f21b5949b5"),
    "name": "Bulbassauro",
    "description": "Chicote de trepadeira",
    "type": "grama",
    "attack": 49,
    "height": 0.4,
    "moves": [
        "folha navalha",
        "chicote de vinha",
        "desvio"
    ]
}
Fetched 1 record(s) in 11ms
```


## Pesquisar **todos** os pokemons que não são do tipo `elétrico`.##
```js
Leonardos-MacBook-Pro(mongod-3.2.0) be-mean-instagram> var query = {type: {$not: /electric/i}}
Leonardos-MacBook-Pro(mongod-3.2.0) be-mean-instagram> db.pokemons.find(query)
{
    "_id": ObjectId("5670bde3dbd364f21b5949b5"),
    "name": "Bulbassauro",
    "description": "Chicote de trepadeira",
    "type": "grama",
    "attack": 49,
    "height": 0.4,
    "moves": [
        "folha navalha",
        "chicote de vinha",
        "desvio"
    ]
}
{
    "_id": ObjectId("5670bde8dbd364f21b5949b6"),
    "name": "Charmander",
    "description": "Esse é o cão chupando manga de fofinho",
    "type": "fogo",
    "attack": 52,
    "height": 0.6,
    "moves": [
        "arranhão",
        "lança chamas",
        "desvio"
    ]
}
{
    "_id": ObjectId("5670bdebdbd364f21b5949b7"),
    "name": "Squirtle",
    "description": "Ejeta água que passarinho não bebe",
    "type": "água",
    "attack": 48,
    "height": 0.5,
    "moves": [
        "jato d'água",
        "chicote de cauda",
        "desvio"
    ]
}
{
    "_id": ObjectId("5670bec5dbd364f21b5949b8"),
    "name": "Caterpie",
    "description": "Larva lutadora",
    "type": "inseto",
    "attack": 30,
    "height": 0.3,
    "defense": 35,
    "moves": [
        "desvio"
    ]
}
{
    "_id": ObjectId("568333b8465179df99fcfdd8"),
    "name": "AindaNaoExisteMon",
    "description": null,
    "type": null,
    "attack": null,
    "defense": null,
    "height": null
}
Fetched 5 record(s) in 12ms
```


## Pesquisar **todos** os pokemons que tenham o ataque `investida` **E** tenham a defesa **não menor ou igual** a 49.##
```js
Leonardos-MacBook-Pro(mongod-3.2.0) be-mean-instagram> var query = {$and: [{moves: {$in: [/investida/i]}}, {attack: {$not: {$lte: 49}}}]}
Leonardos-MacBook-Pro(mongod-3.2.0) be-mean-instagram> db.pokemons.find(query)
Fetched 0 record(s) in 0ms
```


## Remova **todos** os pokemons do tipo água e com attack menor que 50.
```js
Leonardos-MacBook-Pro(mongod-3.2.0) be-mean-instagram> var query = {$and: [{type: /água/i}, {attack: {$lt: 50}}]}
Leonardos-MacBook-Pro(mongod-3.2.0) be-mean-instagram> db.pokemons.remove(query)
Removed 1 record(s) in 11ms
WriteResult({
    "nRemoved": 1
})
```