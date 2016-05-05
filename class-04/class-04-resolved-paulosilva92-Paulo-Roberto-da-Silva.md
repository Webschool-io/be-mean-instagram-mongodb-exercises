# MongoDb - Aula 04 - Exercício
Autor: Paulo Roberto da Silva

## Adicionar 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander

```js
paulo(mongod-3.2.1) be-mean-pokemons> var query = {$or:[{name: /pikachu/i},{name: /squirtle/i}, {name: /bulbassauro/i}, {name: /charmander/i}]}
paulo(mongod-3.2.1) be-mean-pokemons> var mod = {$pushAll : {moves: ['rabada do diabo', 'pézada do capeta']}}
paulo(mongod-3.2.1) be-mean-pokemons> var option = {multi:true}
paulo(mongod-3.2.1) be-mean-pokemons> db.pokemons.update(query, mod, option)
Updated 4 existing record(s) in 20ms
WriteResult({
  "nMatched": 4,
  "nUpserted": 0,
  "nModified": 4
})
paulo(mongod-3.2.1) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56ba032fd930a8178a2e035d"),
  "name": "Bulbassauro",
  "description": "Cara dos cipós",
  "type": "grama",
  "attack": 55,
  "height": 0.4,
  "moves": [
    "golpe 1",
    "golpe 2",
    "rabada do diabo",
    "pézada do capeta"
  ]
}
{
  "_id": ObjectId("56ba032fd930a8178a2e035e"),
  "name": "Charmander",
  "description": "Cara do fogo",
  "type": "fire",
  "attack": 55,
  "height": 0.4,
  "moves": [
    "golpe 1",
    "golpe 2",
    "rabada do diabo",
    "pézada do capeta"
  ]
}
{
  "_id": ObjectId("56ba032fd930a8178a2e035f"),
  "name": "Squirtle",
  "description": "Cara do lava-jato",
  "type": "water",
  "attack": 55,
  "height": 0.4,
  "moves": [
    "golpe 1",
    "golpe 2",
    "rabada do diabo",
    "pézada do capeta"
  ]
}
{
  "_id": ObjectId("56ba0398d930a8178a2e0360"),
  "name": "Pikachu",
  "description": "Rato do fogo",
  "type": "fire",
  "attack": 55,
  "height": 0.4,
  "moves": [
    "golpe 1",
    "golpe 2",
    "rabada do diabo",
    "pézada do capeta"
  ]
}
Fetched 4 record(s) in 6ms
```

## 1 movimento em todos os pokemons: 'desvio'

```js
paulo(mongod-3.2.1) be-mean-pokemons> var query = {}
paulo(mongod-3.2.1) be-mean-pokemons> var mod = {$push:{moves:'desvio'}}
paulo(mongod-3.2.1) be-mean-pokemons> var options = {multi:true}
paulo(mongod-3.2.1) be-mean-pokemons> db.pokemons.update(query, mod, option)
Updated 9 existing record(s) in 2ms
WriteResult({
  "nMatched": 9,
  "nUpserted": 0,
  "nModified": 9
})
paulo(mongod-3.2.1) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56b784d94a6ae70439c45bca"),
  "name": "Butterfree",
  "description": "Its wings, covered with poisonous powders, repel water.",
  "type": "inseto",
  "attack": 45,
  "defense": 50,
  "height": 11,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("56b784d94a6ae70439c45bcb"),
  "name": "Arbok",
  "description": "The frightening patterns on its belly have been studied. Six variations have been confirmed.",
  "type": "veneno",
  "attack": 85,
  "defense": 69,
  "height": 35,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("56b784d94a6ae70439c45bcc"),
  "name": "Ninetales",
  "description": "Its nine tails are said to be imbued with a mystic power. It can live for a thousand years.",
  "type": "fogo",
  "attack": 76,
  "defense": 75,
  "height": 11,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("56b784d94a6ae70439c45bcd"),
  "name": "Grimer",
  "description": "descricao alterada",
  "type": "veneno",
  "attack": 80,
  "defense": 50,
  "height": 9,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("56b784d94a6ae70439c45bce"),
  "name": "PauloMon",
  "description": "Pokemon foda das galacta",
  "type": "veneno",
  "attack": 62,
  "defense": 67,
  "height": 8,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("56ba032fd930a8178a2e035d"),
  "name": "Bulbassauro",
  "description": "Cara dos cipós",
  "type": "grama",
  "attack": 55,
  "height": 0.4,
  "moves": [
    "golpe 1",
    "golpe 2",
    "rabada do diabo",
    "pézada do capeta",
    "desvio"
  ]
}
{
  "_id": ObjectId("56ba032fd930a8178a2e035e"),
  "name": "Charmander",
  "description": "Cara do fogo",
  "type": "fire",
  "attack": 55,
  "height": 0.4,
  "moves": [
    "golpe 1",
    "golpe 2",
    "rabada do diabo",
    "pézada do capeta",
    "desvio"
  ]
}
{
  "_id": ObjectId("56ba032fd930a8178a2e035f"),
  "name": "Squirtle",
  "description": "Cara do lava-jato",
  "type": "water",
  "attack": 55,
  "height": 0.4,
  "moves": [
    "golpe 1",
    "golpe 2",
    "rabada do diabo",
    "pézada do capeta",
    "desvio"
  ]
}
{
  "_id": ObjectId("56ba0398d930a8178a2e0360"),
  "name": "Pikachu",
  "description": "Rato do fogo",
  "type": "fire",
  "attack": 55,
  "height": 0.4,
  "moves": [
    "golpe 1",
    "golpe 2",
    "rabada do diabo",
    "pézada do capeta",
    "desvio"
  ]
}
Fetched 9 record(s) in 9ms

```
## Adicionar o pokemon 'AindaNaoExisteMon' caso ele não exista com todos os dados com o valor 'null' e a descrição 'Sem maiores informações'

```js
paulo(mongod-3.2.1) be-mean-pokemons> var query  = {name:/AindaNaoExisteMon/i}
paulo(mongod-3.2.1) be-mean-pokemons> var mod = {$setOnInsert:   {     name: 'AindaNaoExisteMon',     type: null,     attack: null,     defense: null,     height: null,     description: 'Sem maiores informações'    } }
paulo(mongod-3.2.1) be-mean-pokemons> var options = {upsert: true}
paulo(mongod-3.2.1) be-mean-pokemons> db.pokemons.update(query, mod, options)
Updated 1 new record(s) in 2ms
WriteResult({
  "nMatched": 0,
  "nUpserted": 1,
  "nModified": 0,
  "_id": ObjectId("56ba214c5b885302b79ba418")
})
paulo(mongod-3.2.1) be-mean-pokemons> var query  = {name:/AindaNaoExisteMon/i}
paulo(mongod-3.2.1) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56ba214c5b885302b79ba418"),
  "name": "AindaNaoExisteMon",
  "type": null,
  "attack": null,
  "defense": null,
  "height": null,
  "description": "Sem maiores informações"
}
Fetched 1 record(s) in 2ms

```
## Pesquisar todos os pokemons que possuam o ataque 'investida' e mais um que voce adicionou

```js
paulo(mongod-3.2.1) be-mean-pokemons> var query =  {moves: {$in :['investida', 'rabada do diabo']}}
paulo(mongod-3.2.1) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56ba032fd930a8178a2e035d"),
  "name": "Bulbassauro",
  "description": "Cara dos cipós",
  "type": "grama",
  "attack": 55,
  "height": 0.4,
  "moves": [
    "golpe 1",
    "golpe 2",
    "rabada do diabo",
    "pézada do capeta",
    "desvio"
  ]
}
{
  "_id": ObjectId("56ba032fd930a8178a2e035e"),
  "name": "Charmander",
  "description": "Cara do fogo",
  "type": "fire",
  "attack": 55,
  "height": 0.4,
  "moves": [
    "golpe 1",
    "golpe 2",
    "rabada do diabo",
    "pézada do capeta",
    "desvio"
  ]
}
{
  "_id": ObjectId("56ba032fd930a8178a2e035f"),
  "name": "Squirtle",
  "description": "Cara do lava-jato",
  "type": "water",
  "attack": 55,
  "height": 0.4,
  "moves": [
    "golpe 1",
    "golpe 2",
    "rabada do diabo",
    "pézada do capeta",
    "desvio"
  ]
}
{
  "_id": ObjectId("56ba0398d930a8178a2e0360"),
  "name": "Pikachu",
  "description": "Rato do fogo",
  "type": "fire",
  "attack": 55,
  "height": 0.4,
  "moves": [
    "golpe 1",
    "golpe 2",
    "rabada do diabo",
    "pézada do capeta",
    "desvio"
  ]
}
Fetched 4 record(s) in 23ms
```
## Pesquisar todos os pokemons que possuam os ataques que voce adicionou

```js
paulo(mongod-3.2.1) be-mean-pokemons> var query =  {moves: {$all :['pézada do capeta', 'rabada do diabo']}}
paulo(mongod-3.2.1) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56ba032fd930a8178a2e035d"),
  "name": "Bulbassauro",
  "description": "Cara dos cipós",
  "type": "grama",
  "attack": 55,
  "height": 0.4,
  "moves": [
    "golpe 1",
    "golpe 2",
    "rabada do diabo",
    "pézada do capeta",
    "desvio"
  ]
}
{
  "_id": ObjectId("56ba032fd930a8178a2e035e"),
  "name": "Charmander",
  "description": "Cara do fogo",
  "type": "fire",
  "attack": 55,
  "height": 0.4,
  "moves": [
    "golpe 1",
    "golpe 2",
    "rabada do diabo",
    "pézada do capeta",
    "desvio"
  ]
}
{
  "_id": ObjectId("56ba032fd930a8178a2e035f"),
  "name": "Squirtle",
  "description": "Cara do lava-jato",
  "type": "water",
  "attack": 55,
  "height": 0.4,
  "moves": [
    "golpe 1",
    "golpe 2",
    "rabada do diabo",
    "pézada do capeta",
    "desvio"
  ]
}
{
  "_id": ObjectId("56ba0398d930a8178a2e0360"),
  "name": "Pikachu",
  "description": "Rato do fogo",
  "type": "fire",
  "attack": 55,
  "height": 0.4,
  "moves": [
    "golpe 1",
    "golpe 2",
    "rabada do diabo",
    "pézada do capeta",
    "desvio"
  ]
}
Fetched 4 record(s) in 4ms
```
## Pesquisar todos que não são do tipo elétrico

```js
paulo(mongod-3.2.1) be-mean-pokemons> var query =  {type: {$not : /elétrico/i}}
paulo(mongod-3.2.1) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56b784d94a6ae70439c45bca"),
  "name": "Butterfree",
  "description": "Its wings, covered with poisonous powders, repel water.",
  "type": "inseto",
  "attack": 45,
  "defense": 50,
  "height": 11,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("56b784d94a6ae70439c45bcb"),
  "name": "Arbok",
  "description": "The frightening patterns on its belly have been studied. Six variations have been confirmed.",
  "type": "veneno",
  "attack": 85,
  "defense": 69,
  "height": 35,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("56b784d94a6ae70439c45bcc"),
  "name": "Ninetales",
  "description": "Its nine tails are said to be imbued with a mystic power. It can live for a thousand years.",
  "type": "fogo",
  "attack": 76,
  "defense": 75,
  "height": 11,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("56b784d94a6ae70439c45bcd"),
  "name": "Grimer",
  "description": "descricao alterada",
  "type": "veneno",
  "attack": 80,
  "defense": 50,
  "height": 9,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("56b784d94a6ae70439c45bce"),
  "name": "PauloMon",
  "description": "Pokemon foda das galacta",
  "type": "veneno",
  "attack": 62,
  "defense": 67,
  "height": 8,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("56ba032fd930a8178a2e035d"),
  "name": "Bulbassauro",
  "description": "Cara dos cipós",
  "type": "grama",
  "attack": 55,
  "height": 0.4,
  "moves": [
    "golpe 1",
    "golpe 2",
    "rabada do diabo",
    "pézada do capeta",
    "desvio"
  ]
}
{
  "_id": ObjectId("56ba032fd930a8178a2e035e"),
  "name": "Charmander",
  "description": "Cara do fogo",
  "type": "fire",
  "attack": 55,
  "height": 0.4,
  "moves": [
    "golpe 1",
    "golpe 2",
    "rabada do diabo",
    "pézada do capeta",
    "desvio"
  ]
}
{
  "_id": ObjectId("56ba032fd930a8178a2e035f"),
  "name": "Squirtle",
  "description": "Cara do lava-jato",
  "type": "water",
  "attack": 55,
  "height": 0.4,
  "moves": [
    "golpe 1",
    "golpe 2",
    "rabada do diabo",
    "pézada do capeta",
    "desvio"
  ]
}
{
  "_id": ObjectId("56ba0398d930a8178a2e0360"),
  "name": "Pikachu",
  "description": "Rato do fogo",
  "type": "fire",
  "attack": 55,
  "height": 0.4,
  "moves": [
    "golpe 1",
    "golpe 2",
    "rabada do diabo",
    "pézada do capeta",
    "desvio"
  ]
}
{
  "_id": ObjectId("56ba214c5b885302b79ba418"),
  "name": "AindaNaoExisteMon",
  "type": null,
  "attack": null,
  "defense": null,
  "height": null,
  "description": "Sem maiores informações"
}
Fetched 10 record(s) in 12ms

```
## Pesquisar todos os pokemons que tenham o ataque 'investida' E tenham a defesa não menor ou igual a 49

```js
paulo(mongod-3.2.1) be-mean-pokemons> var query =  {$and :[{ moves: {$in :['investida'] } },{attack:{$not:{$lte:49}}}]}
paulo(mongod-3.2.1) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56ba0398d930a8178a2e0360"),
  "name": "Pikachu",
  "description": "Rato do fogo",
  "type": "fire",
  "attack": 55,
  "height": 0.4,
  "moves": [
    "golpe 1",
    "golpe 2",
    "rabada do diabo",
    "pézada do capeta",
    "desvio",
    "investida"
  ]
}
Fetched 1 record(s) in 3ms
```

## Remova todos os pokemons do tipo 'agua' e com attack menor que 50.

```js
paulo(mongod-3.2.1) be-mean-pokemons> var query =  {$and : [{type:'water'}, {attack : {$lt:50}}]}
paulo(mongod-3.2.1) be-mean-pokemons> db.pokemons.remove(query)
Removed 0 record(s) in 36ms
WriteResult({
  "nRemoved": 0
})
```

var query =  {$and : [{type:'water'}, {attack : {$lt:50}}]}
