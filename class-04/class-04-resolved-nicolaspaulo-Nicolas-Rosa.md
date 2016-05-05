MongoDB - Aula 04 - Exercício
Autor: **Nicolas de Paulo Rosa**

## Adicionando 2 ataques ao mesmo tempo para os pokemons: pikachu, squirtle, bulbassauro e charmander.(1)

```
var query = {name: {$in: [/squirtle/i, /pikachu/i, /bulbassauro/i, /Charmander/i]}}
var mod = {$pushAll: {moves: ["Golpe da Trevas","Disparo Sônico"]}}
var options = {multi: true}
db.pokemons.update(query, mod, options)
Updated 4 existing record(s) in 3ms
WriteResult({
  "nMatched": 4,
  "nUpserted": 0,
  "nModified": 4
})

```

## Adicionando o movimento "desvio" para todos os pokemons.(2)

```
var query = {}
var mod = {$push: {moves: "desvio"}}
var options = {multi: true}
db.pokemons.update(query, mod, options)
Updated 12 existing record(s) in 3ms
WriteResult({
  "nMatched": 12,
  "nUpserted": 0,
  "nModified": 12
})

```

## Adicionando o pokemon "AindaNaoExisteMon" caso ele não exista com todos os dados com o valor "null" e a descrição "Sem maiores informações".(3)

```
var query = {name: /AindaNaoExisteMon/i}
var mod = {$set: {active: true},$setOnInsert: {name: "AindaNaoExisteMon", type: null, attack: null, height: null, moves: null, description: "Sem maiores informações"}}
var options = {upsert: true}
db.pokemons.update(query, mod, options)
Updated 1 new record(s) in 3ms
WriteResult({
  "nMatched": 0,
  "nUpserted": 1,
  "nModified": 0,
  "_id": ObjectId("565cc275e8c3e5b9d25fa3c9")
})

```

## Pesquisando todos os pokemons que possuem o ataque "investida" e mais que foi adicionado podendo escolher o pokemon favorito.(4)

```
var query = {moves: {$all: [/investida/i, /golpe da trevas/i]}}
db.pokemons.find(query)
{
  "_id": ObjectId("56466df8e3d371685183aeb2"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 53,
  "height": 0.6,
  "active": false,
  "moves": [
    "investida",
    "lança chamas",
    "Golpe da Trevas",
    "Disparo Sônico",
    "desvio"
  ]
}
{
  "_id": ObjectId("5653953ccf685efc858ec3ec"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "Eletric",
  "attack": 55,
  "height": 0.4,
  "active": false,
  "moves": [
    "investida",
    "choque do trovão",
    "Golpe da Trevas",
    "Disparo Sônico",
    "desvio"
  ]
}
{
  "_id": ObjectId("5653ae91cf685efc858ec3ed"),
  "name": "Squirtle",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "active": false,
  "description": "Ejeta água que passarinho não bebe",
  "moves": [
    "investida",
    "hidro bomba",
    "Golpe da Trevas",
    "Disparo Sônico",
    "desvio"
  ]
}
{
  "_id": ObjectId("5653bb90cf685efc858ec3ee"),
  "name": "Bulbassauro",
  "type": "folha",
  "attack": 55,
  "height": 0.8,
  "description": "Atira folhas cortadorasde almas",
  "moves": [
    "folha navalha",
    "investida",
    "Golpe da Trevas",
    "Disparo Sônico",
    "desvio"
  ],
  "active": false
}
Fetched 4 record(s) in 4ms

```

## Pesquisando todos os pokemons que possuem os ataque que adicionei  escolhendo o meu pokemon favorito.(5)

```
var query = {moves: {$in: [/golpe da trevas/i, /disparo sônico/i]}}
db.pokemons.find(query)
{
  "_id": ObjectId("56466df8e3d371685183aeb2"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 53,
  "height": 0.6,
  "active": false,
  "moves": [
    "investida",
    "lança chamas",
    "Golpe da Trevas",
    "Disparo Sônico",
    "desvio"
  ]
}
{
  "_id": ObjectId("5653953ccf685efc858ec3ec"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "Eletric",
  "attack": 55,
  "height": 0.4,
  "active": false,
  "moves": [
    "investida",
    "choque do trovão",
    "Golpe da Trevas",
    "Disparo Sônico",
    "desvio"
  ]
}
{
  "_id": ObjectId("5653ae91cf685efc858ec3ed"),
  "name": "Squirtle",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "active": false,
  "description": "Ejeta água que passarinho não bebe",
  "moves": [
    "investida",
    "hidro bomba",
    "Golpe da Trevas",
    "Disparo Sônico",
    "desvio"
  ]
}
{
  "_id": ObjectId("5653bb90cf685efc858ec3ee"),
  "name": "Bulbassauro",
  "type": "folha",
  "attack": 55,
  "height": 0.8,
  "description": "Atira folhas cortadorasde almas",
  "moves": [
    "folha navalha",
    "investida",
    "Golpe da Trevas",
    "Disparo Sônico",
    "desvio"
  ],
  "active": false
}
Fetched 4 record(s) in 6ms

```

## Pesquisar todos pokemons que não são do tipo "Eletric".(6)

```
var query = {type: {$not: /eletric/i}}
db.pokemons.find(query)
{
  "_id": ObjectId("56468586e3d371685183aeb5"),
  "name": "Caterpie",
  "description": "Larva Lutadora",
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
  "_id": ObjectId("564bb0c9367c08688474b4c5"),
  "description": "ALterei de forma diferente passando por variável",
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
  "_id": ObjectId("56534fddcf685efc858ec3e5"),
  "name": "Confusion",
  "description": "Psiquico das loucura",
  "type": "psiquico",
  "attack": 120,
  "height": 5.9,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("5653503dcf685efc858ec3e7"),
  "name": "Fire Blast",
  "description": "Explosão de fogo",
  "type": "fogo",
  "attack": 23,
  "height": 0.2,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("5653503dcf685efc858ec3e8"),
  "name": "Aqua Tail",
  "description": "Cauda de água",
  "type": "água",
  "attack": 65,
  "height": 1.9,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("5653503dcf685efc858ec3ea"),
  "name": "Confusion",
  "description": "Psiquico das loucura",
  "type": "psiquico",
  "attack": 120,
  "height": 5.9,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56538bc2569392a46d194818"),
  "active": false,
  "name": "NaoExisteMon",
  "attack": null,
  "defense": null,
  "height": null,
  "description": "Sem maiores informações",
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56466df8e3d371685183aeb2"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 53,
  "height": 0.6,
  "active": false,
  "moves": [
    "investida",
    "lança chamas",
    "Golpe da Trevas",
    "Disparo Sônico",
    "desvio"
  ]
}
{
  "_id": ObjectId("5653ae91cf685efc858ec3ed"),
  "name": "Squirtle",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "active": false,
  "description": "Ejeta água que passarinho não bebe",
  "moves": [
    "investida",
    "hidro bomba",
    "Golpe da Trevas",
    "Disparo Sônico",
    "desvio"
  ]
}
{
  "_id": ObjectId("5653bb90cf685efc858ec3ee"),
  "name": "Bulbassauro",
  "type": "folha",
  "attack": 55,
  "height": 0.8,
  "description": "Atira folhas cortadorasde almas",
  "moves": [
    "folha navalha",
    "investida",
    "Golpe da Trevas",
    "Disparo Sônico",
    "desvio"
  ],
  "active": false
}
{
  "_id": ObjectId("565cc185e8c3e5b9d25fa3c8"),
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("565cc275e8c3e5b9d25fa3c9"),
  "active": true,
  "name": "AindaNaoExisteMon",
  "type": null,
  "attack": null,
  "height": null,
  "moves": null,
  "description": "Sem maiores informações"
}
Fetched 12 record(s) in 7ms

```

## Pesquisando todos pokemons que tem o ataque "investida" E tenham a defesa não menor ou igual a 49.(7)

```
var query = {$and: [{moves: {$in: [/investida/i]}},{defense: {$not: {$lte: 49}}}]}
db.pokemons.find(query)
{
  "_id": ObjectId("564bb0c9367c08688474b4c5"),
  "description": "ALterei de forma diferente passando por variável",
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
  "_id": ObjectId("56534fddcf685efc858ec3e5"),
  "name": "Confusion",
  "description": "Psiquico das loucura",
  "type": "psiquico",
  "attack": 120,
  "height": 5.9,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("5653503dcf685efc858ec3e7"),
  "name": "Fire Blast",
  "description": "Explosão de fogo",
  "type": "fogo",
  "attack": 23,
  "height": 0.2,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("5653503dcf685efc858ec3e8"),
  "name": "Aqua Tail",
  "description": "Cauda de água",
  "type": "água",
  "attack": 65,
  "height": 1.9,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("5653503dcf685efc858ec3e9"),
  "name": "Electro Ball",
  "description": "Bola elétrica motherfucker",
  "type": "Eletric",
  "attack": 666,
  "height": 1.3,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("5653503dcf685efc858ec3ea"),
  "name": "Confusion",
  "description": "Psiquico das loucura",
  "type": "psiquico",
  "attack": 120,
  "height": 5.9,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56538bc2569392a46d194818"),
  "active": false,
  "name": "NaoExisteMon",
  "attack": null,
  "defense": null,
  "height": null,
  "description": "Sem maiores informações",
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56466df8e3d371685183aeb2"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 53,
  "height": 0.6,
  "active": false,
  "moves": [
    "investida",
    "lança chamas",
    "Golpe da Trevas",
    "Disparo Sônico",
    "desvio"
  ],
  "defense": 88
}
{
  "_id": ObjectId("5653953ccf685efc858ec3ec"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "Eletric",
  "attack": 55,
  "height": 0.4,
  "active": false,
  "moves": [
    "investida",
    "choque do trovão",
    "Golpe da Trevas",
    "Disparo Sônico",
    "desvio"
  ]
}
{
  "_id": ObjectId("5653ae91cf685efc858ec3ed"),
  "name": "Squirtle",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "active": false,
  "description": "Ejeta água que passarinho não bebe",
  "moves": [
    "investida",
    "hidro bomba",
    "Golpe da Trevas",
    "Disparo Sônico",
    "desvio"
  ]
}
{
  "_id": ObjectId("5653bb90cf685efc858ec3ee"),
  "name": "Bulbassauro",
  "type": "folha",
  "attack": 55,
  "height": 0.8,
  "description": "Atira folhas cortadorasde almas",
  "moves": [
    "folha navalha",
    "investida",
    "Golpe da Trevas",
    "Disparo Sônico",
    "desvio"
  ],
  "active": false
}
Fetched 11 record(s) in 14ms

```

## Removendo todos pokemons do tipo água e com ataque menor que 50.(8)

```
var query = {$and: [{type: {$in: [/água/]}}, {attack: {$lt: 50}}]}
db.pokemons.remove(query)
WriteResult({
  "nRemoved": 1
})

```
