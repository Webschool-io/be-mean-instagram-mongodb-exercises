# MongoDB - Aula 04 - Exercício

Autor: Nicolas Serrato

## Adicionar 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.

```js
var query = {name: /Pikachu/i}
var mod = {$pushAll: {moves: ['esfera elétrica', 'investida trovão']}}
db.pokemons.update(query, mod)

var query = {name: /Squirtle/i}
var mod = {$pushAll: {moves: ['raio de gelo', 'giro rápido']}}
db.pokemons.update(query, mod)

var query = {name: /Bulbassauro/i}
var mod = {$pushAll: {moves: ['raio solar', 'dança de pétalas']}}
db.pokemons.update(query, mod)

var query = {name: /Charmander/i}
var mod = {$pushAll: {moves: ['brasas', 'encarar']}}
db.pokemons.update(query, mod)
```

## Adicionar 1 movimento em todos os pokemons: desvio.

```js
var query = {}
var mod = {$push: {moves: 'desvio'}}
var options = {multi: true}
db.pokemons.update(query, mod, options)	
```

## Adicionar o pokemon AindaNaoExisteMon caso ele não exista com todos os dados com o valor null e a descrição: "Sem maiores informações".

```js
var query = {name: /AindaNaoExisteMon/i}
var mod = {$setOnInsert:
    {
      name: 'AindaNaoExisteMon',
      type: null,
      attack: null,
      defense: null,
      height: null,
      description: 'Sem maiores informações'
    }
}
var options = {upsert: true}
db.pokemons.update(query, mod, options)
```

## Pesquisar todos o pokemons que possuam o ataque investida e mais um que você adicionou, escolha seu pokemon favorito.

```js
var query = {moves: {$in: [/investida/i, /desvio/i]}}
db.pokemons.find(query)
{
  "_id": ObjectId("587c325b58c60dbd067167b6"),
  "attack": 30,
  "defense": 30,
  "description": "Fire",
  "height": 1.1,
  "moves": [
    "desvio"
  ],
  "name": "Charmeleon"
}
{
  "_id": ObjectId("587c325b58c60dbd067167b7"),
  "attack": 30,
  "defense": 40,
  "description": "Water",
  "height": 1,
  "moves": [
    "desvio"
  ],
  "name": "Wartortle"
}
{
  "_id": ObjectId("587c325b58c60dbd067167b8"),
  "attack": 30,
  "defense": 30,
  "description": "Grass, Poison",
  "height": 1,
  "moves": [
    "desvio"
  ],
  "name": "Ivysaur"
}
{
  "_id": ObjectId("587c325b58c60dbd067167b9"),
  "attack": 10,
  "defense": 30,
  "description": "Bug",
  "height": 0.7,
  "moves": [
    "desvio"
  ],
  "name": "Metapod"
}
{
  "_id": ObjectId("587c325b58c60dbd067167ba"),
  "attack": 10,
  "defense": 20,
  "description": "Bug, Poison",
  "height": 0.6,
  "moves": [
    "desvio"
  ],
  "name": "Kakuna"
}
{
  "_id": ObjectId("587d2ab7a83165806b92aa8d"),
  "attack": 84,
  "defense": 78,
  "description": "Fire",
  "height": 1.7,
  "moves": [
    "desvio"
  ],
  "name": "Charizard"
}
{
  "_id": ObjectId("587d2ab7a83165806b92aa8e"),
  "attack": 45,
  "defense": 50,
  "description": "Flying",
  "height": 1.09,
  "moves": [
    "desvio"
  ],
  "name": "Butterfree"
}
{
  "_id": ObjectId("587d2ab7a83165806b92aa8f"),
  "attack": 80,
  "defense": 75,
  "description": "Flying",
  "height": 1.5,
  "moves": [
    "desvio"
  ],
  "name": "Pidgeot"
}
{
  "_id": ObjectId("587d2ab7a83165806b92aa90"),
  "attack": 56,
  "defense": 35,
  "description": "Normal",
  "height": 0.3,
  "moves": [
    "desvio"
  ],
  "name": "Rattatá"
}
{
  "_id": ObjectId("587d2ab7a83165806b92aa91"),
  "attack": 81,
  "defense": 60,
  "description": "Normal",
  "height": 0.71,
  "moves": [
    "desvio"
  ],
  "name": "Raticate"
}
{
  "_id": ObjectId("587e47f75e204d1cdc0433d1"),
  "attack": 30,
  "defense": 20,
  "description": "Grass, Poison",
  "heigth": 0.7,
  "moves": [
    "desvio"
  ],
  "name": "Bulbasaur"
}
{
  "_id": ObjectId("587e47f75e204d1cdc0433d2"),
  "attack": 30,
  "defense": 30,
  "description": "Water",
  "heigth": 0.5,
  "moves": [
    "desvio"
  ],
  "name": "Squirtle"
}
{
  "_id": ObjectId("587e47f75e204d1cdc0433d3"),
  "attack": 30,
  "defense": 20,
  "description": "Fire",
  "heigth": 0.6,
  "moves": [
    "desvio"
  ],
  "name": "Charmander"
}
{
  "_id": ObjectId("587e47f75e204d1cdc0433d5"),
  "attack": 40,
  "defense": 40,
  "description": "Water",
  "heigth": 1.6,
  "moves": [
    "desvio"
  ],
  "name": "Blastoise"
}
{
  "_id": ObjectId("587e47f75e204d1cdc0433d4"),
  "attack": 30,
  "defense": 20,
  "description": "Electric",
  "heigth": 0.4,
  "moves": [
    "esfera elétrica",
    "investida trovão",
    "desvio"
  ],
  "name": "Pikachu"
}
Fetched 15 record(s) in 25ms
```

## Pesquisar todos os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.

```js
var query = {moves: {$all: [/mega kick/i]}}
db.pokemons.find(query)
{
  "_id": ObjectId("587e4c7b5e204d1cdc0433d6"),
  "attack": 60,
  "defense": 40,
  "description": "Psychic",
  "heigth": 2,
  "moves": [
    "Mega Punch",
    "Mega Kick"
  ],
  "name": "Mewtwo"
}
Fetched 1 record(s) in 5ms
```
## Pesquisar todos os pokemons que não são do tipo elétrico.

```js
var query = {description: {$not: /Electric/i}}
db.pokemons.find(query)
{
  "_id": ObjectId("587c325b58c60dbd067167b6"),
  "attack": 30,
  "defense": 30,
  "description": "Fire",
  "height": 1.1,
  "moves": [
    "desvio"
  ],
  "name": "Charmeleon"
}
{
  "_id": ObjectId("587c325b58c60dbd067167b7"),
  "attack": 30,
  "defense": 40,
  "description": "Water",
  "height": 1,
  "moves": [
    "desvio"
  ],
  "name": "Wartortle"
}
{
  "_id": ObjectId("587c325b58c60dbd067167b8"),
  "attack": 30,
  "defense": 30,
  "description": "Grass, Poison",
  "height": 1,
  "moves": [
    "desvio"
  ],
  "name": "Ivysaur"
}
{
  "_id": ObjectId("587c325b58c60dbd067167b9"),
  "attack": 10,
  "defense": 30,
  "description": "Bug",
  "height": 0.7,
  "moves": [
    "desvio"
  ],
  "name": "Metapod"
}
{
  "_id": ObjectId("587c325b58c60dbd067167ba"),
  "attack": 10,
  "defense": 20,
  "description": "Bug, Poison",
  "height": 0.6,
  "moves": [
    "desvio"
  ],
  "name": "Kakuna"
}
{
  "_id": ObjectId("587d2ab7a83165806b92aa8d"),
  "attack": 84,
  "defense": 78,
  "description": "Fire",
  "height": 1.7,
  "moves": [
    "desvio"
  ],
  "name": "Charizard"
}
{
  "_id": ObjectId("587d2ab7a83165806b92aa8e"),
  "attack": 45,
  "defense": 50,
  "description": "Flying",
  "height": 1.09,
  "moves": [
    "desvio"
  ],
  "name": "Butterfree"
}
{
  "_id": ObjectId("587d2ab7a83165806b92aa8f"),
  "attack": 80,
  "defense": 75,
  "description": "Flying",
  "height": 1.5,
  "moves": [
    "desvio"
  ],
  "name": "Pidgeot"
}
{
  "_id": ObjectId("587d2ab7a83165806b92aa90"),
  "attack": 56,
  "defense": 35,
  "description": "Normal",
  "height": 0.3,
  "moves": [
    "desvio"
  ],
  "name": "Rattatá"
}
{
  "_id": ObjectId("587d2ab7a83165806b92aa91"),
  "attack": 81,
  "defense": 60,
  "description": "Normal",
  "height": 0.71,
  "moves": [
    "desvio"
  ],
  "name": "Raticate"
}
{
  "_id": ObjectId("587e47f75e204d1cdc0433d1"),
  "attack": 30,
  "defense": 20,
  "description": "Grass, Poison",
  "heigth": 0.7,
  "moves": [
    "desvio"
  ],
  "name": "Bulbasaur"
}
{
  "_id": ObjectId("587e47f75e204d1cdc0433d2"),
  "attack": 30,
  "defense": 30,
  "description": "Water",
  "heigth": 0.5,
  "moves": [
    "desvio"
  ],
  "name": "Squirtle"
}
{
  "_id": ObjectId("587e47f75e204d1cdc0433d3"),
  "attack": 30,
  "defense": 20,
  "description": "Fire",
  "heigth": 0.6,
  "moves": [
    "desvio"
  ],
  "name": "Charmander"
}
{
  "_id": ObjectId("587e47f75e204d1cdc0433d5"),
  "attack": 40,
  "defense": 40,
  "description": "Water",
  "heigth": 1.6,
  "moves": [
    "desvio"
  ],
  "name": "Blastoise"
}
{
  "_id": ObjectId("587e4a637de519c0279e8ac4"),
  "attack": null,
  "defense": null,
  "description": "Sem maiores informações",
  "height": null,
  "name": "AindaNaoExisteMon",
  "type": null
}
{
  "_id": ObjectId("587e4c7b5e204d1cdc0433d6"),
  "attack": 60,
  "defense": 40,
  "description": "Psychic",
  "heigth": 2,
  "moves": [
    "Mega Punch",
    "Mega Kick"
  ],
  "name": "Mewtwo"
}
Fetched 16 record(s) in 9ms
```
## Pesquisar todos os pokemons que tenham o ataque investida E tenham a defesa não menor ou igual a 49.

```js
var query = {$and: [ {moves: {$in: ['investida']}}, {defense: {$not: {$lte: 49}}} ]}
db.pokemons.find(query)
Fetched 0 record(s) in 0ms
```

## Remova todos os pokemons do tipo água E com attack menor que 50.

```js
var query = {$and: [ {description: /water/i}, {attack: {$lt: 50}} ]}
db.pokemons.remove(query)
Removed 3 record(s) in 2ms
```

