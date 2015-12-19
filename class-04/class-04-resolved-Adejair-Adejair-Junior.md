# MongoDB - Aula 04 - Exercício
autor: Adejair Júnior

## **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.
``` JavaScript
var query = {
  $or: [
    {name: 'Pikachu'},
    {name: 'Squirtle'},
    {name: 'Bulbassauro'},
    {name: 'Charmander'}
  ]
}

var mod = {$set: {
  moves: ['Esquivar', 'Bater']
}}

var options = {
  multi: true
}


db.pokemons.update(query, mod, options)

WriteResult({
  "nMatched": 3,
  "nUpserted": 0,
  "nModified": 3
})

Updated 3 existing record(s) in 451ms
// 3 results
// Bulbassauro não existe.
```
## **Adicionar** 1 movimento em todos os pokemons: `desvio`.##

``` JavaScript
var mod = {$push: {
  moves: 'desvio'
}}
var options = {upsert: true, multi: true}

db.pokemons.update({}, mod, options)

WriteResult({
  "nMatched": 610,
  "nUpserted": 0,
  "nModified": 610
})
```

## **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".##
``` JavaScript
var query = {name: 'AindaNaoExisteMon'}
var mod = {$setOnInsert: {
  name: 'AindaNaoExisteMon',
  attack: null,
  defense: null,
  heigth: null,
  hp: null,
  speed: null,
  types: null,
  description: 'Sem maiores informações'
}}

var opt = {upsert: true}

db.pokemons.update(query, mod, opt)

updated 1 new record(s) in 9ms
WriteResult({
  "nMatched": 0,
  "nUpserted": 1,
  "nModified": 0,
  "_id": ObjectId("56547253b56dce8ab96e469c")
})
```

## Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.##
``` JavaScript
var query = {moves: {$in: ['investida']}}

var poke = {
  name: 'Adejair',
  moves: ['investida']
}

db.pokemons.insert(poke)

Inserted 1 record(s) in 4ms
WriteResult({
  "nInserted": 1
})


db.pokemons.find(query)

junior(mongod-3.0.7) be-mean-test> db.pokemons.find(query)
{
  "_id": ObjectId("5654736811a70e10f1f2c99a"),
  "name": "Adejair",
  "moves": [
    "investida"
  ]
}
Fetched 1 record(s) in 23ms

```

## Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.##
```JavaScript

``` JavaScript
var query = {moves: {$in: ['desvio', 'Esquivar', 'Bater']}}
db.pokemons.find(query)

Fetched 20 record(s) in 21ms
```
## Pesquisar **todos** os pokemons que não são do tipo `elétrico`.##

``` JavaScript
var query = {types: {$in: ['electric']}}

db.pokemons.find(query)

junior(mongod-3.0.7) be-mean-test> db.pokemons.find(query)
{
  "_id": ObjectId("564b1dae25337263280d0484"),
  "attack": 35,
  "created": "2013-11-03T15:05:41.435237",
  "defense": 70,
  "height": "3",
  "hp": 25,
  "name": "Magnemite",
  "speed": 45,
  "types": [
    "steel",
    "electric"
  ],
  "active": false,
  "moves": [
    "opressive",
    "desvio"
  ]
}
{
  "_id": ObjectId("564b1dae25337263280d0485"),
  "attack": 60,
  "created": "2013-11-03T15:05:41.437483",
  "defense": 95,
  "height": "10",
  "hp": 50,
  "name": "Magneton",
  "speed": 70,
  "types": [
    "steel",
    "electric"
  ],
  "active": false,
  "moves": [
    "opressive",
    "desvio"
  ]
}
{
  "_id": ObjectId("564b1db125337263280d04a7"),
  "attack": 55,
  "created": "2013-11-03T15:05:41.317235",
  "defense": 40,
  "height": "4",
  "hp": 35,
  "name": "Pikachu",
  "speed": 90,
  "types": [
    "electric"
  ],
  "active": false,
  "moves": [
    "Esquivar",
    "Bater",
    "desvio"
  ]
}
{
  "_id": ObjectId("564b1db125337263280d04a9"),
  "attack": 90,
  "created": "2013-11-03T15:05:41.318944",
  "defense": 55,
  "height": "8",
  "hp": 60,
  "name": "Raichu",
  "speed": 110,
  "types": [
    "electric"
  ],
  "active": false,
  "moves": [
    "opressive",
    "desvio"
  ]
}
{
  "_id": ObjectId("564b1dbb25337263280d04fc"),
  "attack": 83,
  "created": "2013-11-03T15:05:41.511238",
  "defense": 57,
  "height": "11",
  "hp": 65,
  "name": "Electabuzz",
  "speed": 105,
  "types": [
    "electric"
  ],
  "active": false,
  "moves": [
    "opressive",
    "desvio"
  ]
}
{
  "_id": ObjectId("564b1dbb25337263280d0503"),
  "attack": 65,
  "created": "2013-11-03T15:05:41.528778",
  "defense": 60,
  "height": "8",
  "hp": 65,
  "name": "Jolteon",
  "speed": 130,
  "types": [
    "electric"
  ],
  "active": false,
  "moves": [
    "opressive",
    "desvio"
  ]
}
{
  "_id": ObjectId("564b1dbd25337263280d0512"),
  "attack": 63,
  "created": "2013-11-03T15:05:41.696801",
  "defense": 37,
  "height": "6",
  "hp": 45,
  "name": "Elekid",
  "speed": 95,
  "types": [
    "electric"
  ],
  "active": false,
  "moves": [
    "opressive",
    "desvio"
  ]
}
{
  "_id": ObjectId("564b1dbe25337263280d051a"),
  "attack": 75,
  "created": "2013-11-03T15:05:41.608119",
  "defense": 85,
  "height": "14",
  "hp": 90,
  "name": "Ampharos",
  "speed": 55,
  "types": [
    "electric"
  ],
  "active": false,
  "moves": [
    "opressive",
    "desvio"
  ]
}
{
  "_id": ObjectId("564b1dc125337263280d053b"),
  "attack": 85,
  "created": "2013-11-03T15:05:42.005438",
  "defense": 49,
  "height": "9",
  "hp": 60,
  "name": "Luxio",
  "speed": 60,
  "types": [
    "electric"
  ],
  "active": false,
  "moves": [
    "opressive",
    "desvio"
  ]
}
{
  "_id": ObjectId("564b1dc125337263280d053c"),
  "attack": 120,
  "created": "2013-11-03T15:05:42.006958",
  "defense": 79,
  "height": "14",
  "hp": 80,
  "name": "Luxray",
  "speed": 70,
  "types": [
    "electric"
  ],
  "active": false,
  "moves": [
    "opressive",
    "desvio"
  ]
}
{
  "_id": ObjectId("564b1dbd25337263280d0516"),
  "attack": 85,
  "created": "2013-11-03T15:05:41.705705",
  "defense": 75,
  "height": "19",
  "hp": 90,
  "name": "Raikou",
  "speed": 115,
  "types": [
    "electric"
  ],
  "active": false,
  "moves": [
    "opressive",
    "desvio"
  ]
}
{
  "_id": ObjectId("564b1dc425337263280d055d"),
  "attack": 90,
  "created": "2013-11-03T15:05:41.546340",
  "defense": 85,
  "height": "16",
  "hp": 90,
  "name": "Zapdos",
  "speed": 100,
  "types": [
    "flying",
    "electric"
  ],
  "active": false,
  "moves": [
    "opressive",
    "desvio"
  ]
}
{
  "_id": ObjectId("564b1dc825337263280d0575"),
  "attack": 58,
  "created": "2013-11-03T15:05:41.591538",
  "defense": 58,
  "height": "12",
  "hp": 125,
  "name": "Lanturn",
  "speed": 67,
  "types": [
    "water",
    "electric"
  ],
  "active": false,
  "moves": [
    "opressive",
    "desvio"
  ]
}
{
  "_id": ObjectId("564b1dc825337263280d0574"),
  "attack": 38,
  "created": "2013-11-03T15:05:41.589626",
  "defense": 38,
  "height": "5",
  "hp": 75,
  "name": "Chinchou",
  "speed": 67,
  "types": [
    "water",
    "electric"
  ],
  "active": false,
  "moves": [
    "opressive",
    "desvio"
  ]
}
{
  "_id": ObjectId("564b1dc825337263280d0576"),
  "attack": 40,
  "created": "2013-11-03T15:05:41.593051",
  "defense": 15,
  "height": "3",
  "hp": 20,
  "name": "Pichu",
  "speed": 60,
  "types": [
    "electric"
  ],
  "active": false,
  "moves": [
    "opressive",
    "desvio"
  ]
}
{
  "_id": ObjectId("564b1dc825337263280d057c"),
  "attack": 40,
  "created": "2013-11-03T15:05:41.605094",
  "defense": 40,
  "height": "6",
  "hp": 55,
  "name": "Mareep",
  "speed": 35,
  "types": [
    "electric"
  ],
  "active": false,
  "moves": [
    "opressive",
    "desvio"
  ]
}
{
  "_id": ObjectId("564b1dca25337263280d058e"),
  "attack": 30,
  "created": "2013-11-03T15:05:41.470928",
  "defense": 50,
  "height": "5",
  "hp": 40,
  "name": "Voltorb",
  "speed": 100,
  "types": [
    "electric"
  ],
  "active": false,
  "moves": [
    "opressive",
    "desvio"
  ]
}
{
  "_id": ObjectId("564b1dca25337263280d058f"),
  "attack": 50,
  "created": "2013-11-03T15:05:41.472484",
  "defense": 70,
  "height": "12",
  "hp": 60,
  "name": "Electrode",
  "speed": 140,
  "types": [
    "electric"
  ],
  "active": false,
  "moves": [
    "opressive",
    "desvio"
  ]
}
{
  "_id": ObjectId("564b1dcb25337263280d0597"),
  "attack": 123,
  "created": "2013-11-03T15:05:42.100410",
  "defense": 67,
  "height": "18",
  "hp": 75,
  "name": "Electivire",
  "speed": 95,
  "types": [
    "electric"
  ],
  "active": false,
  "moves": [
    "opressive",
    "desvio"
  ]
}
{
  "_id": ObjectId("564b1dcd25337263280d05a8"),
  "attack": 65,
  "created": "2013-11-03T15:05:42.003721",
  "defense": 34,
  "height": "5",
  "hp": 45,
  "name": "Shinx",
  "speed": 45,
  "types": [
    "electric"
  ],
  "active": false,
  "moves": [
    "opressive",
    "desvio"
  ]
}


```

## Pesquisar **todos** os pokemons que tenham o ataque `investida` **E** tenham a defesa **não menor ou igual** a 49.##
``` JavaScript
var query = {
  $and: [
    {
      moves: {$in: ['investida']}
    },
    {
      defense: {$not: {$lte: 49}}
    }
  ]
}

db.pokemons.find(query)

```

## Remova **todos** os pokemons do tipo água e com attack menor que 50.
``` JavaScript
var query = {
  $and: [
    {types: {$in:['water']}},
    {attack: {$lt: 50}}
  ]
}

db.pokemons.remove(query)

Removed 21 record(s) in 270ms
WriteResult({
  "nRemoved": 21
})


```
