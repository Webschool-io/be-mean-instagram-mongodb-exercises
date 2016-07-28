# MongoDB - Aula 04 - Exercício

Autor: Patrick Adelino

## 1. Adicionar 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Bulbasaur, Squirtle, Chamander

```
var query = {name: {$in: ["Pikachu","Bulbasaur","Charmander", "Squirtle"] }}

pontocom-Aspire-4252(mongod-3.2.7) be-mean-pokemon> query
{
  "name": {
    "$in": [
      "Pikachu",
      "Bulbasaur",
      "Charmander",
      "Squirtle"
    ]
  }
}
 var mod = {$pushAll: {moves: ["Investida", "Ataque Rapido"]}}
 {
   "$pushAll": {
     "moves": [
       "Investida",
       "Ataque Rapido"
     ]
   }
 }
 var options = {multi : true}
 {
   "multi": true
 }

 pontocom-Aspire-4252(mongod-3.2.7) be-mean-pokemon> db.pokemons.update(query, mod, options)
 Updated 4 existing record(s) in 96ms
 WriteResult({
   "nMatched": 4,
   "nUpserted": 0,
   "nModified": 4
 })

```

## 2. Adicionar 1 movimento em todos os pokemons: "Desvio"

```
pontocom-Aspire-4252(mongod-3.2.7) be-mean-pokemon> var query = {}
pontocom-Aspire-4252(mongod-3.2.7) be-mean-pokemon> query
{
  
}
pontocom-Aspire-4252(mongod-3.2.7) be-mean-pokemon> var mod = {$push: {moves: "Desvio"}}
pontocom-Aspire-4252(mongod-3.2.7) be-mean-pokemon> mod
{
  "$push": {
    "moves": [
      "Desvio"
    ]
  }
}
var options = {multi : true}
 {
   "multi": true
 }
pontocom-Aspire-4252(mongod-3.2.7) be-mean-pokemon> db.pokemons.update(query, mod, options)
Updated 9 existing record(s) in 3ms
WriteResult({
  "nMatched": 9,
  "nUpserted": 0,
  "nModified": 9
})
```

## 3. Adicionar o Pokemon NaoExisteMon caso ele não exista com todos os dados com o valor null e a descrição: "Sem Maiores Informações"

```
var query = {name: "NaoExisteMon"}
{
  "name": "NaoExisteMon"
}
var mod = {
  $setOnInsert: { 
    "name": "NaoExisteMon",
    "description": "Sem Maiores Informações",
    "attack": null,
    "defense": null,
    "height": null,
    "moves": null        
  }
}
var options = {upsert: true}
{
  upsert: true
}

pontocom-Aspire-4252(mongod-3.2.7) be-mean-pokemon> db.pokemons.update(query,mod, options)
Updated 1 new record(s) in 598ms
WriteResult({
  "nMatched": 0,
  "nUpserted": 1,
  "nModified": 0,
  "_id": ObjectId("5785c27a67f22e2f09650e62")
})
pontocom-Aspire-4252(mongod-3.2.7) be-mean-pokemon> db.pokemons.find(query)
{
  "_id": ObjectId("5785c27a67f22e2f09650e62"),
  "name": "NaoExisteMon",
  "description": "Sem Maiores Informações",
  "attack": null,
  "defense": null,
  "height": null,
  "moves": null
}

```

## 4. Pesquisar todos os pokemons que possuam o ataque 'investida' e um outro que você adicionar, escolher seu pokemon favorito

```
pontocom-Aspire-4252(mongod-3.2.7) be-mean-pokemons> var query = {moves: { $in: ["Investida", "Nightmare"]} }
pontocom-Aspire-4252(mongod-3.2.7) be-mean-pokemons> query
{
  "moves": {
    "$in": [
      "Investida",
      "Nightmare"
    ]
  }
}
pontocom-Aspire-4252(mongod-3.2.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5784309e9fc95fecf503fec1"),
  "name": "Bulbasaur",
  "description": "Bulbasaur é um pokemon pokemon do tipo planta.",
  "attack": 100,
  "defense": 200,
  "height": 0.7,
  "moves": [
    "Investida",
    "Ataque Rapido"
  ]
}
{
  "_id": ObjectId("5784309f9fc95fecf503fec2"),
  "name": "Gengar",
  "description": "Gengar é um pokemon boladão do tipo Ghost.",
  "attack": 300,
  "defense": 300,
  "height": 4.5,
  "moves": [
    "Investida",
    "Ataque Rapido"
  ]
}
{
  "_id": ObjectId("5784309f9fc95fecf503fec3"),
  "name": "Steelix",
  "description": "Evolução do Onix, versão pica e do tipo Steel.",
  "attack": 460,
  "defense": 600,
  "height": 30.2,
  "moves": [
    "Investida",
    "Ataque Rapido"
  ]
}
{
  "_id": ObjectId("5784309f9fc95fecf503fec4"),
  "name": "Hypno",
  "description": "Tem um turbante na cabeça e é amarelinho.",
  "attack": 400,
  "defense": 100,
  "height": 3.9,
  "moves": [
    "Investida",
    "Ataque Rapido",
    "Nightmare"
  ]
}
{
  "_id": ObjectId("5784309f9fc95fecf503fec5"),
  "name": "Fearow",
  "description": "Um ave bem louca, evolução da spearow.",
  "attack": 300,
  "defense": 300,
  "height": 7.8,
  "moves": [
    "Investida",
    "Ataque Rapido"
  ]
}

```

## 5. Pesquisar todos os pokemons que possuam os ataques que voce adicionou, escolha seu pokemon favorito.

```
pontocom-Aspire-4252(mongod-3.2.7) be-mean-pokemons> var query = {moves: {$ne: null}}
pontocom-Aspire-4252(mongod-3.2.7) be-mean-pokemons> query
{
  "moves": {
    "$ne": null
  }
}
pontocom-Aspire-4252(mongod-3.2.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5784309e9fc95fecf503fec1"),
  "name": "Bulbasaur",
  "description": "Bulbasaur é um pokemon pokemon do tipo planta.",
  "attack": 100,
  "defense": 200,
  "height": 0.7,
  "moves": [
    "Investida",
    "Ataque Rapido"
  ]
}
{
  "_id": ObjectId("5784309f9fc95fecf503fec2"),
  "name": "Gengar",
  "description": "Gengar é um pokemon boladão do tipo Ghost.",
  "attack": 300,
  "defense": 300,
  "height": 4.5,
  "moves": [
    "Investida",
    "Ataque Rapido"
  ]
}
{
  "_id": ObjectId("5784309f9fc95fecf503fec3"),
  "name": "Steelix",
  "description": "Evolução do Onix, versão pica e do tipo Steel.",
  "attack": 460,
  "defense": 600,
  "height": 30.2,
  "moves": [
    "Investida",
    "Ataque Rapido"
  ]
}
{
  "_id": ObjectId("5784309f9fc95fecf503fec4"),
  "name": "Hypno",
  "description": "Tem um turbante na cabeça e é amarelinho.",
  "attack": 400,
  "defense": 100,
  "height": 3.9,
  "moves": [
    "Investida",
    "Ataque Rapido",
    "Nightmare"
  ]
}
{
  "_id": ObjectId("5784309f9fc95fecf503fec5"),
  "name": "Fearow",
  "description": "Um ave bem louca, evolução da spearow.",
  "attack": 300,
  "defense": 300,
  "height": 7.8,
  "moves": [
    "Investida",
    "Ataque Rapido"
  ]
}
Fetched 5 record(s) in 13ms

```

## 6. Pesquisar todos os pokemons que não sao do tipo 'elétrico'

```
pontocom-Aspire-4252(mongod-3.2.7) be-mean-pokemons> var query = {type: {$ne: "elétrico"}}
pontocom-Aspire-4252(mongod-3.2.7) be-mean-pokemons> query
{
  "type": {
    "$ne": "elétrico"
  }
}
pontocom-Aspire-4252(mongod-3.2.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5784309e9fc95fecf503fec1"),
  "name": "Bulbasaur",
  "description": "Bulbasaur é um pokemon pokemon do tipo planta.",
  "attack": 100,
  "defense": 200,
  "height": 0.7,
  "moves": [
    "Investida",
    "Ataque Rapido"
  ]
}
{
  "_id": ObjectId("5784309f9fc95fecf503fec2"),
  "name": "Gengar",
  "description": "Gengar é um pokemon boladão do tipo Ghost.",
  "attack": 300,
  "defense": 300,
  "height": 4.5,
  "moves": [
    "Investida",
    "Ataque Rapido"
  ]
}
{
  "_id": ObjectId("5784309f9fc95fecf503fec3"),
  "name": "Steelix",
  "description": "Evolução do Onix, versão pica e do tipo Steel.",
  "attack": 460,
  "defense": 600,
  "height": 30.2,
  "moves": [
    "Investida",
    "Ataque Rapido"
  ]
}
{
  "_id": ObjectId("5784309f9fc95fecf503fec4"),
  "name": "Hypno",
  "description": "Tem um turbante na cabeça e é amarelinho.",
  "attack": 400,
  "defense": 100,
  "height": 3.9,
  "moves": [
    "Investida",
    "Ataque Rapido",
    "Nightmare"
  ]
}
{
  "_id": ObjectId("5784309f9fc95fecf503fec5"),
  "name": "Fearow",
  "description": "Um ave bem louca, evolução da spearow.",
  "attack": 300,
  "defense": 300,
  "height": 7.8,
  "moves": [
    "Investida",
    "Ataque Rapido"
  ]
}
Fetched 5 record(s) in 12ms
```

## 7. Pesquisar todos os pokemons que tenham o ataque investida E tenham a defesa não menor ou igual a 49

```
pontocom-Aspire-4252(mongod-3.2.7) be-mean-pokemons> var query = {$and: [{moves: {$in: ["Investida"]}}, {defense: {$gte: 49}}]}
pontocom-Aspire-4252(mongod-3.2.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5784309e9fc95fecf503fec1"),
  "name": "Bulbasaur",
  "description": "Bulbasaur é um pokemon pokemon do tipo planta.",
  "attack": 100,
  "defense": 200,
  "height": 0.7,
  "moves": [
    "Investida",
    "Ataque Rapido"
  ]
}
{
  "_id": ObjectId("5784309f9fc95fecf503fec2"),
  "name": "Gengar",
  "description": "Gengar é um pokemon boladão do tipo Ghost.",
  "attack": 300,
  "defense": 300,
  "height": 4.5,
  "moves": [
    "Investida",
    "Ataque Rapido"
  ]
}
{
  "_id": ObjectId("5784309f9fc95fecf503fec3"),
  "name": "Steelix",
  "description": "Evolução do Onix, versão pica e do tipo Steel.",
  "attack": 460,
  "defense": 600,
  "height": 30.2,
  "moves": [
    "Investida",
    "Ataque Rapido"
  ]
}
{
  "_id": ObjectId("5784309f9fc95fecf503fec4"),
  "name": "Hypno",
  "description": "Tem um turbante na cabeça e é amarelinho.",
  "attack": 400,
  "defense": 100,
  "height": 3.9,
  "moves": [
    "Investida",
    "Ataque Rapido",
    "Nightmare"
  ]
}
{
  "_id": ObjectId("5784309f9fc95fecf503fec5"),
  "name": "Fearow",
  "description": "Um ave bem louca, evolução da spearow.",
  "attack": 300,
  "defense": 300,
  "height": 7.8,
  "moves": [
    "Investida",
    "Ataque Rapido"
  ]
}
Fetched 5 record(s) in 16ms
```

## 8. Remova todos os pokemons do tipo água e com o attack menor que 50
```
pontocom-Aspire-4252(mongod-3.2.7) be-mean-pokemons> var query = {$and: [{type: "água"},{attack: {$lt: 50}}]}
pontocom-Aspire-4252(mongod-3.2.7) be-mean-pokemons> query
{
  "$and": [
    {
      "type": "água"
    },
    {
      "attack": {
        "$lt": 50
      }
    }
  ]
}
pontocom-Aspire-4252(mongod-3.2.7) be-mean-pokemons> db.pokemons.remove(query)
Removed 0 record(s) in 3ms
WriteResult({
  "nRemoved": 0
})
```
