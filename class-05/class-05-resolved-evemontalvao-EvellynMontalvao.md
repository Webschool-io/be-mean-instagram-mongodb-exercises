# MongoDB - Aula 04 - Exercício
Autor: Evellyn Montalvão

## Adicionar 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.

```
var query = {nome: 'pikachu'}
var moves = ['thunder shock','magnet rise','fusion bolt']
var mod = {$pushAll: {move: moves}

db.pokemons.update(query, mod)
Updated 1 existing record(s) in 2ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})

db.pokemons.find(query)
{
  "_id": ObjectId("57b16d7697fb7ea051e2cabf"),
  "nome": "pikachu",
  "description": "Eletric one",
  "attack": 30,
  "defense": 20,
  "height": 0.4,
  "type": "eletric",
  "move":
    [
      "thunder shock",
      "magnet rise",
      "fusion bolt"
    ]
}

var query = {nome: 'charmander'}
var moves = ['searing shot','flare blitz','heat wave']
db.pokemons.update(query, mod)
Updated 1 existing record(s) in 2ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})
db.pokemons.find(query)
{
  "_id": ObjectId("57b16e1397fb7ea051e2cac2"),
  "nome": "charmander",
  "description": "the dragon one",
  "attack": 30,
  "defense": 20,
  "height": 0.6,
  "type": "fire",
  "move": [
    "searing shot",
    "flare blitz",
    "heat wave"
  ]
}

var moves = ['brine','soak','water gun']
var query = {nome: 'squirtle'}
db.pokemons.update(query, mod)
Updated 1 existing record(s) in 1ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})
db.pokemons.find(query)
{
  "_id": ObjectId("57b16df297fb7ea051e2cac1"),
  "nome": "squirtle",
  "description": "turtle one",
  "attack": 40,
  "defense": 30,
  "height": 0.5,
  "type": "water",
  "move": [
    "searing shot",
    "flare blitz",
    "heat wave"
  ]
}
Fetched 1 record(s) in 1ms

var moves = ['grass knot','power whip','seed bomb']
var query = {nome: 'bulbasaur'}
db.pokemons.update(query, mod)
Updated 1 existing record(s) in 1ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})
db.pokemons.find(query)
{
  "_id": ObjectId("57b16e2297fb7ea051e2cac3"),
  "nome": "bulbasaur",
  "description": "the frog one",
  "attack": 30,
  "defense": 20,
  "height": 0.7,
  "type": "grass",
  "move": [
    "searing shot",
    "flare blitz",
    "heat wave"
  ]
}
Fetched 1 record(s) in 1ms


```

## Adicionar 1 movimento em todos os pokemons: desvio.

```
var query = {}
var mod = {$push: {move: 'desvio'}}
var options = {multi: true}
db.pokemons.update(query, mod, options)
Updated 14 existing record(s) in 1ms
WriteResult({
  "nMatched": 14,
  "nUpserted": 0,
  "nModified": 14
})


```

## Adicionar o pokemon AindaNaoExisteMon caso ele não exista com todos os dados com o valor null e a descrição: "Sem maiores informações".

```
var query = {nome:/AindaNaoExisteMon/i}
var mod = {$setOnInsert: {nome: "AindaNaoExisteMon", description: 'Sem maiores informações', attack: null, defense: null, height: null, type: null}}
var options = {upsert: true}
db.pokemons.update(query, mod, options)
Updated 1 new record(s) in 1ms
WriteResult({
  "nMatched": 0,
  "nUpserted": 1,
  "nModified": 0,
  "_id": ObjectId("57b1f03838a5e27b2eb77769")
})

```

## Pesquisar todos o pokemons que possuam o ataque desvio (nenhum dos meus tem investida) e mais um que você adicionou, escolha seu pokemon favorito.

```
var query = {move:{$in: ['investida','heat wave']}}
db.pokemons.find(query)
{
  "_id": ObjectId("57afe503ef96c0ea464330d5"),
  "nome": "dragonair",
  "description": "Dragonair stores an enormous amount of energy inside its body",
  "attack": 80,
  "defense": 30,
  "height": 4,
  "type": "dragon",
  "move": [
    "searing shot",
    "flare blitz",
    "heat wave",
    "desvio"
  ]
}


```
## Pesquisar todos os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.

```
var query = {move:{$in: ['searing shot','heat wave','flare blitz']}}
db.pokemons.find(query)
{
  "_id": ObjectId("57b16e1397fb7ea051e2cac2"),
  "nome": "charmander",
  "description": "the dragon one",
  "attack": 30,
  "defense": 20,
  "height": 0.6,
  "type": "fire",
  "move": [
    "searing shot",
    "flare blitz",
    "heat wave",
    "desvio"
  ]
}

```

## Pesquisar todos os pokemons que não são do tipo elétrico.

```

var query = {type: {$not: 'eletric'}}
db.pokemons.find(query)
Error: error: {
  "$err": "Can't canonicalize query: BadValue $not needs a regex or a document",
  "code": 17287
}
var query = {type: {$not: /eletric/i}}
db.pokemons.find(query)
{
  "_id": ObjectId("57afe680ef96c0ea464330d6"),
  "nome": "aurorus",
  "description": "The diamond-shaped crystals body",
  "attack": 40,
  "defense": 30,
  "height": 2.4,
  "type": "rock",
  "move": [
    "desvio"
  ]
}
{
  "_id": ObjectId("57afe737ef96c0ea464330d7"),
  "nome": "reshiram",
  "description": "This legendary Pokémon can scorch the world with fire",
  "attack": 60,
  "defense": 40,
  "height": 3.2,
  "type": "fire",
  "move": [
    "desvio"
  ]
}
{
  "_id": ObjectId("57afe73eef96c0ea464330d8"),
  "nome": "archeops",
  "description": "They are intelligent and will cooperate to catch prey",
  "attack": 70,
  "defense": 30,
  "height": 1.4,
  "type": "rock",
  "move": [
    "desvio"
  ]
}
{
  "_id": ObjectId("57afe745ef96c0ea464330d9"),
  "nome": "liepard",
  "description": "They run silently in the night.",
  "attack": 50,
  "defense": 20,
  "height": 1.1,
  "type": "dark",
  "move": [
    "desvio"
  ]
}
{
  "_id": ObjectId("57afe74eef96c0ea464330da"),
  "nome": "emboar",
  "description": "It cares deeply about its friends.",
  "attack": 60,
  "defense": 30,
  "height": 1.6,
  "type": "fire",
  "move": [
    "desvio"
  ]
}
{
  "_id": ObjectId("57afe75cef96c0ea464330db"),
  "nome": "tangrowth",
  "description": "It ensnares prey by extending arms made of vines. ",
  "attack": 50,
  "defense": 50,
  "height": 2,
  "type": "grass",
  "move": [
    "desvio"
  ]
}
{
  "_id": ObjectId("57afe7edef96c0ea464330dc"),
  "nome": "margmortar",
  "description": "It blasts fireballs of over 3,600 degrees Fahrenheit ",
  "attack": 50,
  "defense": 30,
  "height": 1.6,
  "type": "fire",
  "move": [
    "desvio"
  ]
}
{
  "_id": ObjectId("57afe7f6ef96c0ea464330dd"),
  "nome": "weavile",
  "description": "It lives in snowy regions",
  "attack": 60,
  "defense": 30,
  "height": 1.1,
  "type": "ice",
  "move": [
    "desvio"
  ]
}
{
  "_id": ObjectId("57afe7fdef96c0ea464330de"),
  "nome": "eevee",
  "description": "The pokemon that has my name",
  "attack": 30,
  "defense": 20,
  "height": 0.3,
  "type": "normal",
  "move": [
    "desvio"
  ]
}
{
  "_id": ObjectId("57b16df297fb7ea051e2cac1"),
  "nome": "squirtle",
  "description": "turtle one",
  "attack": 40,
  "defense": 30,
  "height": 0.5,
  "type": "water",
  "move": [
    "searing shot",
    "flare blitz",
    "heat wave",
    "desvio"
  ]
}
{
  "_id": ObjectId("57b16e1397fb7ea051e2cac2"),
  "nome": "charmander",
  "description": "the dragon one",
  "attack": 30,
  "defense": 20,
  "height": 0.6,
  "type": "fire",
  "move": [
    "searing shot",
    "flare blitz",
    "heat wave",
    "desvio"
  ]
}
{
  "_id": ObjectId("57b16e2297fb7ea051e2cac3"),
  "nome": "bulbasaur",
  "description": "the frog one",
  "attack": 30,
  "defense": 20,
  "height": 0.7,
  "type": "grass",
  "move": [
    "searing shot",
    "flare blitz",
    "heat wave",
    "desvio"
  ]
}
{
  "_id": ObjectId("57afe503ef96c0ea464330d5"),
  "nome": "dragonair",
  "description": "Dragonair stores an enormous amount of energy inside its body",
  "attack": 80,
  "defense": 30,
  "height": 4,
  "type": "dragon",
  "move": [
    "searing shot",
    "flare blitz",
    "heat wave",
    "desvio"
  ]
}
{
  "_id": ObjectId("57b1f03838a5e27b2eb77769"),
  "nome": "AindaNaoExisteMon",
  "description": null,
  "attack": null,
  "defense": null,
  "height": null,
  "type": null
}

```

## Pesquisar todos pokemons que tenham o ataque investida E tenham a defesa não menor ou igual a 49.

var query = {$and: [{move: {$in: [/desvio/i]}}, {attack: {$not: {$lte: 49}}}]}
db.pokemons.find(query)
```
{
  "_id": ObjectId("57afe737ef96c0ea464330d7"),
  "nome": "reshiram",
  "description": "This legendary Pokémon can scorch the world with fire",
  "attack": 60,
  "defense": 40,
  "height": 3.2,
  "type": "fire",
  "move": [
    "desvio"
  ]
}
{
  "_id": ObjectId("57afe73eef96c0ea464330d8"),
  "nome": "archeops",
  "description": "They are intelligent and will cooperate to catch prey",
  "attack": 70,
  "defense": 30,
  "height": 1.4,
  "type": "rock",
  "move": [
    "desvio"
  ]
}
{
  "_id": ObjectId("57afe745ef96c0ea464330d9"),
  "nome": "liepard",
  "description": "They run silently in the night.",
  "attack": 50,
  "defense": 20,
  "height": 1.1,
  "type": "dark",
  "move": [
    "desvio"
  ]
}
{
  "_id": ObjectId("57afe74eef96c0ea464330da"),
  "nome": "emboar",
  "description": "It cares deeply about its friends.",
  "attack": 60,
  "defense": 30,
  "height": 1.6,
  "type": "fire",
  "move": [
    "desvio"
  ]
}
{
  "_id": ObjectId("57afe75cef96c0ea464330db"),
  "nome": "tangrowth",
  "description": "It ensnares prey by extending arms made of vines. ",
  "attack": 50,
  "defense": 50,
  "height": 2,
  "type": "grass",
  "move": [
    "desvio"
  ]
}
{
  "_id": ObjectId("57afe7edef96c0ea464330dc"),
  "nome": "margmortar",
  "description": "It blasts fireballs of over 3,600 degrees Fahrenheit ",
  "attack": 50,
  "defense": 30,
  "height": 1.6,
  "type": "fire",
  "move": [
    "desvio"
  ]
}
{
  "_id": ObjectId("57afe7f6ef96c0ea464330dd"),
  "nome": "weavile",
  "description": "It lives in snowy regions",
  "attack": 60,
  "defense": 30,
  "height": 1.1,
  "type": "ice",
  "move": [
    "desvio"
  ]
}
{
  "_id": ObjectId("57afe503ef96c0ea464330d5"),
  "nome": "dragonair",
  "description": "Dragonair stores an enormous amount of energy inside its body",
  "attack": 80,
  "defense": 30,
  "height": 4,
  "type": "dragon",
  "move": [
    "searing shot",
    "flare blitz",
    "heat wave",
    "desvio"
  ]
}

```

## Remova todos os pokemons do tipo água e com attack menor que 50.

```
var query = {$and: [{type: 'water'},{attack: {$lt: 50}}]}
db.pokemons.remove(query)
Removed 1 record(s) in 2ms
WriteResult({
  "nRemoved": 1
})
```