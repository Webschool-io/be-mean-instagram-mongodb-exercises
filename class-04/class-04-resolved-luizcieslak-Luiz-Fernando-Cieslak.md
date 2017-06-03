# MongoDB - Aula 04 - Exercício
autor: Luiz Fernando Cieslak

## 1. Adicionar 2 ataques ao mesmo tempo aos pokemons: Pikachu, Oddish e Starmie

```
var attacks = ['tackle','growl']
var query = {$or: [{name: /pikachu/i}, {name: /starmie/i}, {name: /oddish/i}]}
var mod = {$push : {moves : {$each: attacks} } }
var options = {multi: true}
db.pokemons.update(query,mod,options)

Updated 3 existing record(s) in 1ms
WriteResult({
  "nMatched": 3,
  "nUpserted": 0,
  "nModified": 3
})
```

## 2. Adicionar 1 movimento para todos os pokemons: `desvio`
```
var query = {} //todos
var mod = { $push: {moves: 'desvio'} } //ou mod = {$set: {moves:['investida']}}
var options = {multi: true}
db.pokemons.update(query, mod, options)

Updated 5 existing record(s) in 1ms
WriteResult({
  "nMatched": 5,
  "nUpserted": 0,
  "nModified": 5
})
```

## 3. Adicionar o pokemon `AindaNaoExisteMon` caso ele nao exista com todos os dados com o valor `null` e a desc: "Sem maiores info"

```
var query = {name: /AindaNaoExisteMon/i}
var mod = {
  $setOnInsert: {name: "AindaNaoExisteMon", attack: null, defense: null, height: null, description: "Sem maiores informações"}
}
var options = {upsert: true}
db.pokemons.update(query, mod, options)
```
## 4. Pesquisar todos os pokemos que possuam `investida` e `hidro bomba`

```
var query = {moves: {$all:[/hidro bomba/i,/investida/i]}}
db.pokemons.find(query)

{
  "_id": ObjectId("57db1d927933407799dc5d1a"),
  "name": "Starmie",
  "description": "estrela de 8 pontas roxa que solta agua",
  "type": "agua",
  "attack": 80,
  "defense": 50,
  "height": 0.6,
  "moves": [
    "investida",
    "hidro bomba",
    "tackle",
    "growl",
    "desvio"
  ]
}

```

## 4. Pesquisar todos os pokemos que possuam `tackle` e `growl`

```
var query = {moves: {$all:[/tackle/i,/growl/i]}}
db.pokemons.find(query)

{
  "_id": ObjectId("57db1d877933407799dc5d19"),
  "name": "Oddish",
  "description": "planta verde mt louca",
  "type": "grama",
  "attack": 60,
  "defense": 30,
  "height": 0.3,
  "moves": [
    "investida",
    "folha navalha",
    "tackle",
    "growl",
    "desvio"
  ]
}
{
  "_id": ObjectId("57db1d637933407799dc5d18"),
  "name": "Pikachu",
  "description": "pokemon amarelo que solta raio pela bochecha",
  "type": "electric",
  "attack": 55,
  "defense": 20,
  "height": 0.4,
  "moves": [
    "choque do trovao",
    "ataque rápido",
    "investida",
    "tackle",
    "growl",
    "desvio"
  ]
}
{
  "_id": ObjectId("57db1d927933407799dc5d1a"),
  "name": "Starmie",
  "description": "estrela de 8 pontas roxa que solta agua",
  "type": "agua",
  "attack": 80,
  "defense": 50,
  "height": 0.6,
  "moves": [
    "investida",
    "hidro bomba",
    "tackle",
    "growl",
    "desvio"
  ]
}
Fetched 3 record(s) in 0ms
```

## 6. Pesquisar todos que nao sao do tipo `electric`
```
var query = {type: {$ne:'electric'}}
db.pokemons.find(query)

{
  "_id": ObjectId("57db1d877933407799dc5d19"),
  "name": "Oddish",
  "description": "planta verde mt louca",
  "type": "grama",
  "attack": 60,
  "defense": 30,
  "height": 0.3,
  "moves": [
    "investida",
    "folha navalha",
    "tackle",
    "growl",
    "desvio"
  ]
}
{
  "_id": ObjectId("57db1df04db19953af64a73d"),
  "name": "Metapod",
  "description": "casulo inquebravel",
  "type": "grama",
  "attack": 32,
  "defense": 60,
  "height": 0.4,
  "moves": [
    "investida",
    "endurecer",
    "desvio"
  ]
}
{
  "_id": ObjectId("57db1e6d4db19953af64a73e"),
  "name": "Polygon",
  "description": "pato feito em origami",
  "type": "psychic",
  "attack": 90,
  "defense": 60,
  "height": 0.4,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("57db1d927933407799dc5d1a"),
  "name": "Starmie",
  "description": "estrela de 8 pontas roxa que solta agua",
  "type": "agua",
  "attack": 80,
  "defense": 50,
  "height": 0.6,
  "moves": [
    "investida",
    "hidro bomba",
    "tackle",
    "growl",
    "desvio"
  ]
}
{
  "_id": ObjectId("57df7bcafc5cbe2b8b0d2f36"),
  "name": "AindaNaoExisteMon",
  "attack": null,
  "defense": null,
  "height": null,
  "description": "Sem maiores informações"
}
Fetched 5 record(s) in 1ms

```

## 7. Pesquisar todos que tenham o ataque `investida` e defesa <= 49
```
var query = {$and: [{moves :{$in:[/investida/i]}}, {defense: {$lte:49}}]}
db.pokemons.find(query)

{
  "_id": ObjectId("57db1d877933407799dc5d19"),
  "name": "Oddish",
  "description": "planta verde mt louca",
  "type": "grama",
  "attack": 60,
  "defense": 30,
  "height": 0.3,
  "moves": [
    "investida",
    "folha navalha",
    "tackle",
    "growl",
    "desvio"
  ]
}
{
  "_id": ObjectId("57db1d637933407799dc5d18"),
  "name": "Pikachu",
  "description": "pokemon amarelo que solta raio pela bochecha",
  "type": "electric",
  "attack": 55,
  "defense": 20,
  "height": 0.4,
  "moves": [
    "choque do trovao",
    "ataque rápido",
    "investida",
    "tackle",
    "growl",
    "desvio"
  ]
}
Fetched 2 record(s) in 2ms
```

## 8. Remova todos os pokemons do tipo agua e com attack < 50
```
var query = {$and:[{type:"agua"},{attack:{$lt:50}}]}
db.pokemons.remove(query)

Removed 0 record(s) in 3ms
WriteResult({
  "nRemoved": 0
})

```
