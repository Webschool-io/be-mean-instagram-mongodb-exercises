# MongoDB - Aula 02 - Exercício
autor: Gustavo Cardoso

## Adicionar 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander

```
var query = {
  $or: [
    {name: /pikachu/i},
    {name: /charmander/i},
    {name: /squirtle/i},
    {name: /bulbassauro/i}
  ]
};
var mod = {$pushAll: {moves: ['raio de lava', 'lança chamas']}};
var options = {multi: true};

db.pokemons.update(query, mod, options);

Updated 4 existing record(s) in 2ms
WriteResult({
  "nMatched": 4,
  "nUpserted": 0,
  "nModified": 4
})
```

## Adicionar 1 movimento em todos os pokemons: desvio

```
var query = {};
var mod = {$push: {moves: "desvio"}};
var options = {multi: true};

db.pokemons.update(query, mod, options);

Updated 13 existing record(s) in 2ms
WriteResult({
  "nMatched": 13,
  "nUpserted": 0,
  "nModified": 13
})
```

## Adicionar o pokemon AindaNaoExisteMon caso ele não exista com todos os dados com o valor null e a descrição: "Sem maiores informações"

```
var query = {name: /AindaNaoExisteMon/i};
var mod = {
  "$setOnInsert": {
    "name": "AindaNaoExisteMon",
    "attack": null,
    "height": null,
    "defense": null,
    "moves": [ ],
    "description": "Sem maiores informações"
  }
};
var options = {upsert: true};

db.pokemons.update(query, mod, options);

Updated 1 new record(s) in 2ms
WriteResult({
  "nMatched": 0,
  "nUpserted": 1,
  "nModified": 0,
  "_id": ObjectId("5654adfe97b434844a409ff9")
})
```

## Pesquisar todos o pokemons que possuam o ataque investida e mais um que você adicionou, escolha seu pokemon favorito

```
var query = {
  moves: {
    $in: [
      /investida/i,
      /lamina raivosa/i
    ]
  }
};

db.pokemons.find(query);

{
  "_id": ObjectId("56440f66a511bc2dc25a2e53"),
  "name": "Shedinja",
  "description": "A hard body doesn't move",
  "type": "bug",
  "attack": 50,
  "defense": 20,
  "height": 0.4,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56440ffda511bc2dc25a2e54"),
  "name": "Haunter",
  "description": "A dangerous pokemon",
  "type": "ghost",
  "attack": 30,
  "defense": 45,
  "height": 5.03,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("5644103fa511bc2dc25a2e55"),
  "name": "Duskull",
  "description": "Can pass through any wall",
  "type": "ghost",
  "attack": 20,
  "defense": 40,
  "height": 2.07,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("5644108aa511bc2dc25a2e56"),
  "name": "Froslass",
  "description": "A very nice and cute pokemon",
  "type": "ice",
  "attack": 40,
  "defense": 30,
  "height": 4.03,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("564410d5a511bc2dc25a2e57"),
  "name": "Phantump",
  "description": "They prefer to live in abandoned forests",
  "type": "grass",
  "attack": 0.4,
  "defense": 20,
  "height": 0.5,
  "active": false,
  "moves": [
    "investida",
    "folha navalha",
    "desvio"
  ]
}
{
  "_id": ObjectId("564a4c7f648788bb6904987e"),
  "description": "Pokemon de teste",
  "name": "Testemon",
  "attack": 8000,
  "defense": 8000,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56450608522a41dc0db3501c"),
  "name": "Pikachu",
  "description": "A very cute pokemon",
  "type": "electric",
  "attack": 40,
  "defense": 50,
  "height": 0.3,
  "moves": [
    "investida",
    "choque do trovão",
    "raio de lava",
    "lança chamas",
    "desvio"
  ],
  "active": false
}
{
  "_id": ObjectId("56548bee97b434844a409ff8"),
  "active": false,
  "name": "NaoExisteMon",
  "attack": null,
  "defense": null,
  "height": null,
  "description": "Sem maiores infos",
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("5645036ec7211828f46ca310"),
  "name": "Rotom",
  "description": "Research continues on this Pokémon, which could be the power source of a unique motor",
  "type": "electric",
  "attack": 30,
  "defense": 30,
  "height": 0.4,
  "active": false,
  "moves": [
    "investida",
    "lamina raivosa",
    "desvio"
  ]
}
{
  "_id": ObjectId("564503bcc7211828f46ca311"),
  "name": "Yamask",
  "description": "Arose from the spirits of people interred in graves",
  "type": "ghost",
  "attack": 20,
  "defense": 40,
  "height": 0.3,
  "active": false,
  "moves": [
    "investida",
    "hidro bomba",
    "desvio"
  ]
}
Fetched 10 record(s) in 6ms
```

## Pesquisar todos os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.

```
var query = {
  moves: {
    $in: [/desvio/i]
  }
};

db.pokemons.find(query);

{
  "_id": ObjectId("56440f66a511bc2dc25a2e53"),
  "name": "Shedinja",
  "description": "A hard body doesn't move",
  "type": "bug",
  "attack": 50,
  "defense": 20,
  "height": 0.4,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56440ffda511bc2dc25a2e54"),
  "name": "Haunter",
  "description": "A dangerous pokemon",
  "type": "ghost",
  "attack": 30,
  "defense": 45,
  "height": 5.03,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("5644103fa511bc2dc25a2e55"),
  "name": "Duskull",
  "description": "Can pass through any wall",
  "type": "ghost",
  "attack": 20,
  "defense": 40,
  "height": 2.07,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("5644108aa511bc2dc25a2e56"),
  "name": "Froslass",
  "description": "A very nice and cute pokemon",
  "type": "ice",
  "attack": 40,
  "defense": 30,
  "height": 4.03,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("564410d5a511bc2dc25a2e57"),
  "name": "Phantump",
  "description": "They prefer to live in abandoned forests",
  "type": "grass",
  "attack": 0.4,
  "defense": 20,
  "height": 0.5,
  "active": false,
  "moves": [
    "investida",
    "folha navalha",
    "desvio"
  ]
}
{
  "_id": ObjectId("564a4c7f648788bb6904987e"),
  "description": "Pokemon de teste",
  "name": "Testemon",
  "attack": 8000,
  "defense": 8000,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56450608522a41dc0db3501c"),
  "name": "Pikachu",
  "description": "A very cute pokemon",
  "type": "electric",
  "attack": 40,
  "defense": 50,
  "height": 0.3,
  "moves": [
    "investida",
    "choque do trovão",
    "raio de lava",
    "lança chamas",
    "desvio"
  ],
  "active": false
}
{
  "_id": ObjectId("56548bee97b434844a409ff8"),
  "active": false,
  "name": "NaoExisteMon",
  "attack": null,
  "defense": null,
  "height": null,
  "description": "Sem maiores infos",
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("5645036ec7211828f46ca310"),
  "name": "Rotom",
  "description": "Research continues on this Pokémon, which could be the power source of a unique motor",
  "type": "electric",
  "attack": 30,
  "defense": 30,
  "height": 0.4,
  "active": false,
  "moves": [
    "investida",
    "lamina raivosa",
    "desvio"
  ]
}
{
  "_id": ObjectId("56549e70614a97e870e7c4f3"),
  "name": "Bulbassauro",
  "description": "A little mega sauro monster",
  "type": "fire",
  "attack": 45,
  "defense": 35,
  "height": 3,
  "active": false,
  "moves": [
    "raio de lava",
    "lança chamas",
    "desvio"
  ]
}
{
  "_id": ObjectId("56549cc1614a97e870e7c4f2"),
  "name": "Charmander",
  "description": "The flame that burns at the tip of its tail is an indication of its emotions",
  "type": "fire",
  "attack": 30,
  "defense": 20,
  "height": 2,
  "active": false,
  "moves": [
    "raio de lava",
    "lança chamas",
    "desvio"
  ]
}
{
  "_id": ObjectId("564503bcc7211828f46ca311"),
  "name": "Yamask",
  "description": "Arose from the spirits of people interred in graves",
  "type": "ghost",
  "attack": 20,
  "defense": 40,
  "height": 0.3,
  "active": false,
  "moves": [
    "investida",
    "hidro bomba",
    "desvio"
  ]
}
{
  "_id": ObjectId("56549edb614a97e870e7c4f4"),
  "name": "Squirtle",
  "description": "Squirtle's shell is not merely used for protection",
  "type": "water",
  "attack": 30,
  "defense": 30,
  "height": 1.8,
  "active": false,
  "moves": [
    "raio de lava",
    "lança chamas",
    "desvio"
  ]
}
Fetched 13 record(s) in 6ms
```

## Pesquisar todos os pokemons que não são do tipo "elétrico"

```
var query = {type: {$ne: "electric"}};

db.pokemons.find(query);

{
  "_id": ObjectId("56440f66a511bc2dc25a2e53"),
  "name": "Shedinja",
  "description": "A hard body doesn't move",
  "type": "bug",
  "attack": 50,
  "defense": 20,
  "height": 0.4,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56440ffda511bc2dc25a2e54"),
  "name": "Haunter",
  "description": "A dangerous pokemon",
  "type": "ghost",
  "attack": 30,
  "defense": 45,
  "height": 5.03,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("5644103fa511bc2dc25a2e55"),
  "name": "Duskull",
  "description": "Can pass through any wall",
  "type": "ghost",
  "attack": 20,
  "defense": 40,
  "height": 2.07,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("5644108aa511bc2dc25a2e56"),
  "name": "Froslass",
  "description": "A very nice and cute pokemon",
  "type": "ice",
  "attack": 40,
  "defense": 30,
  "height": 4.03,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("564410d5a511bc2dc25a2e57"),
  "name": "Phantump",
  "description": "They prefer to live in abandoned forests",
  "type": "grass",
  "attack": 0.4,
  "defense": 20,
  "height": 0.5,
  "active": false,
  "moves": [
    "investida",
    "folha navalha",
    "desvio"
  ]
}
{
  "_id": ObjectId("564a4c7f648788bb6904987e"),
  "description": "Pokemon de teste",
  "name": "Testemon",
  "attack": 8000,
  "defense": 8000,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56548bee97b434844a409ff8"),
  "active": false,
  "name": "NaoExisteMon",
  "attack": null,
  "defense": null,
  "height": null,
  "description": "Sem maiores infos",
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56549e70614a97e870e7c4f3"),
  "name": "Bulbassauro",
  "description": "A little mega sauro monster",
  "type": "fire",
  "attack": 45,
  "defense": 35,
  "height": 3,
  "active": false,
  "moves": [
    "raio de lava",
    "lança chamas",
    "desvio"
  ]
}
{
  "_id": ObjectId("56549cc1614a97e870e7c4f2"),
  "name": "Charmander",
  "description": "The flame that burns at the tip of its tail is an indication of its emotions",
  "type": "fire",
  "attack": 30,
  "defense": 20,
  "height": 2,
  "active": false,
  "moves": [
    "raio de lava",
    "lança chamas",
    "desvio"
  ]
}
{
  "_id": ObjectId("564503bcc7211828f46ca311"),
  "name": "Yamask",
  "description": "Arose from the spirits of people interred in graves",
  "type": "ghost",
  "attack": 20,
  "defense": 40,
  "height": 0.3,
  "active": false,
  "moves": [
    "investida",
    "hidro bomba",
    "desvio"
  ]
}
{
  "_id": ObjectId("56549edb614a97e870e7c4f4"),
  "name": "Squirtle",
  "description": "Squirtle's shell is not merely used for protection",
  "type": "water",
  "attack": 30,
  "defense": 30,
  "height": 1.8,
  "active": false,
  "moves": [
    "raio de lava",
    "lança chamas",
    "desvio"
  ]
}
{
  "_id": ObjectId("5654adfe97b434844a409ff9"),
  "name": "AindaNaoExisteMon",
  "attack": null,
  "height": null,
  "defense": null,
  "moves": [ ],
  "description": "Sem maiores informações"
}
Fetched 12 record(s) in 6ms
```

## Pesquisar todos os pokemons que tenham o ataque investida E tenham a defesa não menor ou igual a 49

```
var query = {
  $and: [
    {moves: {$in: [/investida/i]}},
    {defense: {$lte: 49}}
  ]
};

db.pokemons.find(query);

{
  "_id": ObjectId("56440f66a511bc2dc25a2e53"),
  "name": "Shedinja",
  "description": "A hard body doesn't move",
  "type": "bug",
  "attack": 50,
  "defense": 20,
  "height": 0.4,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56440ffda511bc2dc25a2e54"),
  "name": "Haunter",
  "description": "A dangerous pokemon",
  "type": "ghost",
  "attack": 30,
  "defense": 45,
  "height": 5.03,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("5644103fa511bc2dc25a2e55"),
  "name": "Duskull",
  "description": "Can pass through any wall",
  "type": "ghost",
  "attack": 20,
  "defense": 40,
  "height": 2.07,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("5644108aa511bc2dc25a2e56"),
  "name": "Froslass",
  "description": "A very nice and cute pokemon",
  "type": "ice",
  "attack": 40,
  "defense": 30,
  "height": 4.03,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("564410d5a511bc2dc25a2e57"),
  "name": "Phantump",
  "description": "They prefer to live in abandoned forests",
  "type": "grass",
  "attack": 0.4,
  "defense": 20,
  "height": 0.5,
  "active": false,
  "moves": [
    "investida",
    "folha navalha",
    "desvio"
  ]
}
{
  "_id": ObjectId("5645036ec7211828f46ca310"),
  "name": "Rotom",
  "description": "Research continues on this Pokémon, which could be the power source of a unique motor",
  "type": "electric",
  "attack": 30,
  "defense": 30,
  "height": 0.4,
  "active": false,
  "moves": [
    "investida",
    "lamina raivosa",
    "desvio"
  ]
}
{
  "_id": ObjectId("564503bcc7211828f46ca311"),
  "name": "Yamask",
  "description": "Arose from the spirits of people interred in graves",
  "type": "ghost",
  "attack": 20,
  "defense": 40,
  "height": 0.3,
  "active": false,
  "moves": [
    "investida",
    "hidro bomba",
    "desvio"
  ]
}
Fetched 7 record(s) in 5ms
```

## Remova todos os pokemons do tipo água e com attack menor que 50

```
var query = {
  $and: [
    {type: /water/i},
    {attack: {$lte: 50}}
  ]
};

db.pokemons.remove(query);

Removed 1 record(s) in 2ms
WriteResult({
  "nRemoved": 1
})
```