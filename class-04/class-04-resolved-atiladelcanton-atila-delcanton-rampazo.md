# MongoDB - Aula 04 - Exercício
autor: Átila Delcanton Rampazo

## Adicionar 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.
``` JavaScript
var query = {$or:[ {name:'Pikachu'}, {name:'Squirtle'}, {name:'Bulbassaur'}, {name:'Charmander'}]}

var attacks = ['Esquivar','Bater']

var mod = {$push : {moves : {$each: attacks} } }

var options = {multi:true}

MacBook-Pro-de-User(mongod-3.2.6) be-mean-instagram> db.pokemons.update(query,mod,options)
Updated 3 existing record(s) in 2ms
WriteResult({
  "nMatched": 3,
  "nUpserted": 0,
  "nModified": 3
})

```

## **Adicionar** 1 movimento em todos os pokemons: `desvio`.##
``` JavaScript
var query = {}
var attacks = ['Desvio']
var mod = {$push:{moves:$each:attacks}}}

db.pokemons.update(query,mod,options)
Updated 5 existing record(s) in 6ms
WriteResult({
  "nMatched": 5,
  "nUpserted": 0,
  "nModified": 5
})
MacBook-Pro-de-User(mongod-3.2.6) be-mean-instagram> db.pokemons.find()
{
  "_id": ObjectId("57784e2b001b7e26ac27522f"),
  "name": "Bulbasaur",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "moves": [
    "Desvio"
  ]
}
{
  "_id": ObjectId("57784e33001b7e26ac275230"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "grama",
  "eletric": 55,
  "height": 0.4,
  "moves": [
    "Esquivar",
    "Bater",
    "Desvio"
  ]
}
{
  "_id": ObjectId("57784e39001b7e26ac275231"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "water",
  "attack": 30,
  "height": 0.5,
  "moves": [
    "Esquivar",
    "Bater",
    "Desvio"
  ]
}
{
  "_id": ObjectId("57784e40001b7e26ac275232"),
  "name": "Abra",
  "description": "Bixin maí liso que politico",
  "type": "psychic",
  "attack": 20,
  "height": 0.9,
  "moves": [
    "Desvio"
  ]
}
{
  "_id": ObjectId("57784e65001b7e26ac275233"),
  "name": "Charmander",
  "description": "Lança Chamas",
  "type": "fire",
  "attack": 20,
  "height": 0.9,
  "moves": [
    "Esquivar",
    "Bater",
    "Desvio"
  ]
}
Fetched 5 record(s) in 9ms


```
##  **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".##

```JavaScript
MacBook-Pro-de-User(mongod-3.2.6) be-mean-instagram> var query = {name: /AindaNaoExisteMon/i}

MacBook-Pro-de-User(mongod-3.2.6) be-mean-instagram> var mod = {$setOnInsert: {name: "AindaNaoExisteMon", attack: null, defense: null, height: null,description: "Sem maiores informações"}}

MacBook-Pro-de-User(mongod-3.2.6) be-mean-instagram> var options = {upsert: true}

MacBook-Pro-de-User(mongod-3.2.6) be-mean-instagram> db.pokemons.update(query, mod, options)
Updated 1 new record(s) in 9ms
WriteResult({
  "nMatched": 0,
  "nUpserted": 1,
  "nModified": 0,
  "_id": ObjectId("577854a182152c3c5acb968e")
})

```

## Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.##

```JavaScript
  
  MacBook-Pro-de-User(mongod-3.2.6) be-mean-instagram> var query  = {moves:{$in:[/desvio/i,/hibro bomba/i]}}

  MacBook-Pro-de-User(mongod-3.2.6) be-mean-instagram> db.pokemons.find(query)

  {
  "_id": ObjectId("57784e39001b7e26ac275231"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "water",
  "attack": 30,
  "height": 0.5,
  "moves": [
    "Esquivar",
    "Bater",
    "Desvio",
    "Hidro Bomba"
  ]
}


```

## Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.##

```JavaScript
  MacBook-Pro-de-User(mongod-3.2.6) be-mean-instagram> var query  = {moves:{$in:[/esquivar/i,/bater/i]}}

  MacBook-Pro-de-User(mongod-3.2.6) be-mean-instagram> db.pokemons.find(query)

  {
  "_id": ObjectId("57784e39001b7e26ac275231"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "water",
  "attack": 30,
  "height": 0.5,
  "moves": [
    "Esquivar",
    "Bater",
    "Desvio",
    "Hidro Bomba"
  ]
}
```
## Pesquisar **todos** os pokemons que não são do tipo `elétrico`.##

```JavaScript

MacBook-Pro-de-User(mongod-3.2.6) be-mean-instagram> var query = {type:/electric/i}
MacBook-Pro-de-User(mongod-3.2.6) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("57785848001b7e26ac275234"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "eletric": 55,
  "height": 0.4,
  "moves": [
    "Esquivar",
    "Bater",
    "Desvio"
  ]
}

```

## Pesquisar **todos** os pokemons que tenham o ataque `investida` **E** tenham a defesa **não menor ou igual** a 49.##

```JavaScript
  
  MacBook-Pro-de-User(mongod-3.2.6) be-mean-instagram> var query = {$and:[{moves:{$in:[/desvio/i]},defense:{$not:{$lte:49}}}]}
  MacBook-Pro-de-User(mongod-3.2.6) be-mean-instagram> db.pokemons.find(query)
  {
    "_id": ObjectId("57784e39001b7e26ac275231"),
    "name": "Squirtle",
    "description": "Ejeta água que passarinho não bebe",
    "type": "water",
    "attack": 30,
    "height": 0.5,
    "moves": [
      "Esquivar",
      "Bater",
      "Desvio",
      "Hidro Bomba"
    ],
    "defense": 820
  }
  {
    "_id": ObjectId("57784e40001b7e26ac275232"),
    "name": "Abra",
    "description": "Bixin maí liso que politico",
    "type": "psychic",
    "attack": 20,
    "height": 0.9,
    "moves": [
      "Desvio"
    ],
    "defense": 120
  }
  {
    "_id": ObjectId("57784e65001b7e26ac275233"),
    "name": "Charmander",
    "description": "Lança Chamas",
    "type": "fire",
    "attack": 20,
    "height": 0.9,
    "moves": [
      "Esquivar",
      "Bater",
      "Desvio"
    ]
  }
  Fetched 3 record(s) in 6ms
```

## Remova **todos** os pokemons do tipo água e com attack menor que 50.

```JavaScript
var query = {$and:[{type:{$in:[/water/i]},attack:{$lt:50}}]}
MacBook-Pro-de-User(mongod-3.2.6) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("57784e39001b7e26ac275231"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "water",
  "attack": 30,
  "height": 0.5,
  "moves": [
    "Esquivar",
    "Bater",
    "Desvio",
    "Hidro Bomba"
  ],
  "defense": 820
}
Fetched 1 record(s) in 2ms
```