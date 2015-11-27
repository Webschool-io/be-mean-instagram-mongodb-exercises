# MongoDB - Aula 04 - Exercício
autor: Jefferson William Machado

## **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.
```js
> var query = {name: /pikachu/i}
> var mod = {$pushAll: {attacks: ['Tail Whip', 'Thunder Shock']}}
> db.pokemons.update(query, mod)
WriteResult({ "nMatched" : 1, "nUpserted" : 0, "nModified" : 1 })
> db.pokemons.find(query)
{
    "_id" : ObjectId("564a7c362c153ed825a6905a"),
    "attack" : 55,
    "created" : "2013-11-03T15:05:41.317235",
    "defense" : 40,
    "height" : "4",
    "hp" : 35,
    "name" : "Pikachu",
    "speed" : 90,
    "types" : [ "electric" ],
    "attacks" : [ "Tail Whip", "Thunder Shock" ]
}

> var query = {name: /Squirtle/i}
> var mod = {$pushAll: {attacks: ['Tackle', 'Tail Whip']}}
> db.pokemons.update(query, mod)
WriteResult({ "nMatched" : 1, "nUpserted" : 0, "nModified" : 1 })
> db.pokemons.find(query)
{
    "_id": ObjectId("564a7c4c2c153ed825a6911d"),
    "attack": 48,
    "created": "2013-11-03T15:05:41.278310",
    "defense": 65,
    "height": "5",
    "hp": 44,
    "name": "Squirtle",
    "speed": 43,
    "types": [ "water" ],
    "attacks": [ "Tackle", "Tail Whip" ]
}

> var query = {name: /Bulbasaur/i}
> var mod = {$pushAll: {attacks: ['Tackle', 'Growl']}}
> db.pokemons.update(query, mod)
WriteResult({ "nMatched" : 1, "nUpserted" : 0, "nModified" : 1 })
> db.pokemons.find(query)
{
    "_id": ObjectId("564a7c702c153ed825a692b7"),
    "attack": 49,
    "created": "2013-11-03T15:05:41.260678",
    "defense": 49,
    "height": "7",
    "hp": 45,
    "name": "Bulbasaur",
    "speed": 45,
    "types": [ "poison", "grass" ],
    "attacks": [ "Tackle", "Growl" ]
}

> var query = {name: /Charmander/i}
> var mod = {$pushAll: {attacks: ['Growl', 'Scratch']}}
> db.pokemons.update(query, mod)
WriteResult({ "nMatched" : 1, "nUpserted" : 0, "nModified" : 1 })
> db.pokemons.find(query)
{
    "_id": ObjectId("564a7c452c153ed825a690e1"),
    "attack": 52,
    "created": "2013-11-03T15:05:41.271082",
    "defense": 43,
    "height": "6",
    "hp": 39,
    "name": "Charmander",
    "speed": 65,
    "types": [ "fire" ],
    "attacks": [ "Growl", "Scratch" ]
}
```

## **Adicionar** 1 movimento em todos os pokemons: `desvio`.##
```js
> var query = {}
> var mod = {$push: {moves: 'desvio'}}
> var options = {multi: true}
> db.pokemons.update(query, mod, options)
WriteResult({ "nMatched" : 620, "nUpserted" : 0, "nModified" : 620 })
> db.pokemons.findOne({})
{
  "_id" : ObjectId("564a7c362c153ed825a69054"),
  "attack" : 90,
  "created" : "2013-11-03T15:05:41.297180",
  "defense" : 40,
  "height" : "10",
  "hp" : 65,
  "name" : "Beedrill",
  "speed" : 75,
  "types" : [
    "poison",
    "bug"
  ],
  "moves" : [
    "desvio"
  ]
}
```

## **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".##
```js
> var query = {name: 'AindaNaoExisteMon'}
> var mod = {attack: null, created: null, defense: null, height: null, hp: null, name: 'AindaNaoExisteMon', speed: null, types: null, moves: null, description: 'Sem maiores informações'}
> var options = {upsert: true}
> db.pokemons.update(query, mod, options)
WriteResult({
  "nMatched" : 0,
  "nUpserted" : 1,
  "nModified" : 0,
  "_id" : ObjectId("5654e7a2c6eb273670af3470")
})
```

## Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.##
```js
> var query = {attacks: {$all: ['investida', 'Growl']}}
> db.pokemons.find(query)
> 
```

## Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.##
```js
> var query = {attacks: {$all: [/growl/i, /scratch/i]}}
> db.pokemons.find(query)
{
    "_id": ObjectId("564a7c452c153ed825a690e1"),
    "attack": 52,
    "created": "2013-11-03T15:05:41.271082",
    "defense": 43,
    "height": "6",
    "hp": 39,
    "name": "Charmander",
    "speed": 65,
    "types": [ "fire" ],
    "attacks": [ "Growl", "Scratch" ],
    "moves": [ "desvio" ]
}
```

## Pesquisar **todos** os pokemons que não são do tipo `elétrico`.##
``js
```js
> var query = {types: {$nin: [/elétrico/i]}}
> db.pokemons.find(query)
{
    "_id": ObjectId("564a7c362c153ed825a69054"),
    "attack": 90,
    "created": "2013-11-03T15:05:41.297180",
    "defense": 40,
    "height": "10",
    "hp": 65,
    "name": "Beedrill",
    "speed": 75,
    "types": [ "poison", "bug" ],
    "moves": [ "desvio" ]
}
```

## Remova **todos** os pokemons do tipo água e com attack menor que 50.
```js
> var query = {types: {$in: ['água']}, attack: {$lt: 50}}
> db.pokemons.remove(query)
WriteResult({ "nRemoved" : 0 })
```