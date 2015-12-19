# MongoDB - Aula 04 - Exercício
autor: Vinícius Galvão

## **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.
```
MBP-de-Vinicius(mongod-3.0.6) be-mean-instagram> var query = {name: {$in: [/Pikachu/i, /Squirtle/i, /Bulbassauro/i, /Charmander/i]}}
MBP-de-Vinicius(mongod-3.0.6) be-mean-instagram> var mod = {$pushAll: {moves: ['chute matador','paralisia mental']}}
MBP-de-Vinicius(mongod-3.0.6) be-mean-instagram> var opt = {multi: true}
MBP-de-Vinicius(mongod-3.0.6) be-mean-instagram> db.pokemons.update(query, mod, opt)
Updated 4 existing record(s) in 5ms
WriteResult({
  "nMatched": 4,
  "nUpserted": 0,
  "nModified": 4
})
```

## **Adicionar** 1 movimento em todos os pokemons: `desvio`.##
```
MBP-de-Vinicius(mongod-3.0.6) be-mean-instagram> var query = {}
MBP-de-Vinicius(mongod-3.0.6) be-mean-instagram> var mod = {$push: {moves: 'desvio'}}
MBP-de-Vinicius(mongod-3.0.6) be-mean-instagram> var opt = {multi:true}
MBP-de-Vinicius(mongod-3.0.6) be-mean-instagram> db.pokemons.update(query, mod, opt)
Updated 6 existing record(s) in 5ms
WriteResult({
  "nMatched": 6,
  "nUpserted": 0,
  "nModified": 6
})
```
## **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".##
```
MBP-de-Vinicius(mongod-3.0.6) be-mean-instagram> var query = {name: /NaoExisteMon/i}
MBP-de-Vinicius(mongod-3.0.6) be-mean-instagram> var mod = {$set: {active:null}, $setOnInsert: {name: "NaoExisteMon", attack: null, defense: null, height: null, description: "Sem maiores informaçoes"}}
MBP-de-Vinicius(mongod-3.0.6) be-mean-instagram> var opt = {upsert:true}
MBP-de-Vinicius(mongod-3.0.6) be-mean-instagram> db.pokemons.update(query, mod, opt)
Updated 1 new record(s) in 2ms
WriteResult({
  "nMatched": 0,
  "nUpserted": 1,
  "nModified": 0,
  "_id": ObjectId("564f546cbb089ccee84f53b8")
})
```

## Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.##
```
MBP-de-Vinicius(mongod-3.0.6) be-mean-instagram> var query = {moves: {$all: ['investida', 'chute matador']}}
MBP-de-Vinicius(mongod-3.0.6) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("5643583ac1a1390994ce24e5"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "height": 0.4,
  "active": false,
  "moves": [
    "investida",
    "choque do trovão",
    "chute matador",
    "paralisia mental",
    "desvio"
  ]
}
{
  "_id": ObjectId("56435900c1a1390994ce24e7"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "active": false,
  "moves": [
    "investida",
    "lança-chamas",
    "chute matador",
    "paralisia mental",
    "desvio"
  ]
}
{
  "_id": ObjectId("56435974c1a1390994ce24e8"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "active": false,
  "moves": [
    "investida",
    "hidro bomba",
    "chute matador",
    "paralisia mental",
    "desvio"
  ]
}
{
  "_id": ObjectId("564358d3c1a1390994ce24e6"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "active": false,
  "moves": [
    "investida",
    "folha navalha",
    "chute matador",
    "paralisia mental",
    "desvio"
  ]
}
Fetched 4 record(s) in 5ms
```

## Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.##
```
MBP-de-Vinicius(mongod-3.0.6) be-mean-instagram> var query = {moves: {$all: ['paralisia mental', 'chute matador']}}
MBP-de-Vinicius(mongod-3.0.6) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("5643583ac1a1390994ce24e5"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "height": 0.4,
  "active": false,
  "moves": [
    "investida",
    "choque do trovão",
    "chute matador",
    "paralisia mental",
    "desvio"
  ]
}
{
  "_id": ObjectId("56435900c1a1390994ce24e7"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "active": false,
  "moves": [
    "investida",
    "lança-chamas",
    "chute matador",
    "paralisia mental",
    "desvio"
  ]
}
{
  "_id": ObjectId("56435974c1a1390994ce24e8"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "active": false,
  "moves": [
    "investida",
    "hidro bomba",
    "chute matador",
    "paralisia mental",
    "desvio"
  ]
}
{
  "_id": ObjectId("564358d3c1a1390994ce24e6"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "active": false,
  "moves": [
    "investida",
    "folha navalha",
    "chute matador",
    "paralisia mental",
    "desvio"
  ]
}
Fetched 4 record(s) in 5ms
```

## Pesquisar **todos** os pokemons que não são do tipo `elétrico`.##
```
MBP-de-Vinicius(mongod-3.0.6) be-mean-instagram> var query = {type: {$not: /eletric/i}}
MBP-de-Vinicius(mongod-3.0.6) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("56435fe1c1a1390994ce24e9"),
  "name": "Caterpie",
  "description": "Larva lutadora",
  "type": "inseto",
  "attack": 30,
  "height": 0.3,
  "defense": 35,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("564aa86c6baaf9fddecaa8f2"),
  "description": "Pokemon de teste",
  "name": "Testemon",
  "attack": 8000,
  "defense": 8000,
  "moves": [
    "investida",
    "desvio"
  ],
  "active": false
}
{
  "_id": ObjectId("56435900c1a1390994ce24e7"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "active": false,
  "moves": [
    "investida",
    "lança-chamas",
    "chute matador",
    "paralisia mental",
    "desvio"
  ]
}
{
  "_id": ObjectId("56435974c1a1390994ce24e8"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "active": false,
  "moves": [
    "investida",
    "hidro bomba",
    "chute matador",
    "paralisia mental",
    "desvio"
  ]
}
{
  "_id": ObjectId("564358d3c1a1390994ce24e6"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "active": false,
  "moves": [
    "investida",
    "folha navalha",
    "chute matador",
    "paralisia mental",
    "desvio"
  ]
}
{
  "_id": ObjectId("564f546cbb089ccee84f53b8"),
  "active": null,
  "name": "NaoExisteMon",
  "attack": null,
  "defense": null,
  "height": null,
  "description": "Sem maiores informaçoes"
}
Fetched 6 record(s) in 5ms
```

## Pesquisar **todos** os pokemons que tenham o ataque `investida` **E** tenham a defesa **não menor ou igual** a 49.##
```
MBP-de-Vinicius(mongod-3.0.6) be-mean-instagram> var query = {$and: [{moves: {$in: [/investida/i]}}, {defense: {$gt: 49}}]}
MBP-de-Vinicius(mongod-3.0.6) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("564aa86c6baaf9fddecaa8f2"),
  "description": "Pokemon de teste",
  "name": "Testemon",
  "attack": 8000,
  "defense": 8000,
  "moves": [
    "investida",
    "desvio"
  ],
  "active": false
}
Fetched 1 record(s) in 1ms
```

## Remova **todos** os pokemons do tipo água e com attack menor que 50.
```
MBP-de-Vinicius(mongod-3.0.6) be-mean-instagram> var query = {$and: [{type: /água/i}, {attack: {$lt: 50}}]}
MBP-de-Vinicius(mongod-3.0.6) be-mean-instagram> db.pokemons.remove(query)
Removed 1 record(s) in 23ms
WriteResult({
  "nRemoved": 1
})
```
