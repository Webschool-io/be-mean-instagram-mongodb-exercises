# MongoDB - Aula 04 - Exercício
Autor: Mauricio Gravena de Oliveira

## Adicionando 2 ataques ao mesmo tempo para os pokemons

```
mau(mongod-3.2.0-rc3-110-g327660f) be-mean-pokemons> var query = {"_id": ObjectId("5655a6a5f1a7bce768c728e5")}
mau(mongod-3.2.0-rc3-110-g327660f) be-mean-pokemons> var mod = {$pushAll: {moves: ["Static","Lightning Rod"]}}
mau(mongod-3.2.0-rc3-110-g327660f) be-mean-pokemons> db.pokemons.update(query, mod)

mau(mongod-3.2.0-rc3-110-g327660f) be-mean-pokemons> var query = {name: /squirtle/i}
mau(mongod-3.2.0-rc3-110-g327660f) be-mean-pokemons> var mod = {$pushAll: {moves: ["Torrent", "Rain Dish"]}}
mau(mongod-3.2.0-rc3-110-g327660f) be-mean-pokemons> db.pokemons.update(query, mod)

mau(mongod-3.2.0-rc3-110-g327660f) be-mean-pokemons> var query = {name: /bulbasaur/i}
mau(mongod-3.2.0-rc3-110-g327660f) be-mean-pokemons> var mod = {$pushAll: {moves: ["Overgrow", "Chlorophyll"]}}
mau(mongod-3.2.0-rc3-110-g327660f) be-mean-pokemons> db.pokemons.update(query, mod)

mau(mongod-3.2.0-rc3-110-g327660f) be-mean-pokemons> var query = {name: /Charmander/i}
mau(mongod-3.2.0-rc3-110-g327660f) be-mean-pokemons> var mod = {$pushAll: {moves: ["Blaze", "Solar Power"]}}
mau(mongod-3.2.0-rc3-110-g327660f) be-mean-pokemons> db.pokemons.update(query, mod)
```

## Adicionando 1 movimento em todos os pokemons

```
mau(mongod-3.2.0-rc3-110-g327660f) be-mean-pokemons> var query = {}
mau(mongod-3.2.0-rc3-110-g327660f) be-mean-pokemons> var mod = {$push: {moves: "desvio"}}
mau(mongod-3.2.0-rc3-110-g327660f) be-mean-pokemons> var options = {multi: true}
mau(mongod-3.2.0-rc3-110-g327660f) be-mean-pokemons> db.pokemons.update(query, mod, options)
```
## Adicionando o pokemon "AindaNaoExisteMon"

```
mau(mongod-3.2.0-rc3-110-g327660f) be-mean-pokemons> var query = {name: /AindaNaoExisteMon/i}
mau(mongod-3.2.0-rc3-110-g327660f) be-mean-pokemons> var mod = {$set: {active: true}, $setOnInsert: {name: "AindaNaoExisteMon", attack: null, defense: null, height: null, description: "Sem maiores informações"}}
mau(mongod-3.2.0-rc3-110-g327660f) be-mean-pokemons> var options = {upsert: true}
mau(mongod-3.2.0-rc3-110-g327660f) be-mean-pokemons> db.pokemons.update(query, mod, options)
```

## Pesquisando todos com ataque "investida" e mais um favorito

```
mau(mongod-3.2.0-rc3-110-g327660f) be-mean-pokemons> var query = {moves: {$in: [/investida/i, /Blaze/i]}}
mau(mongod-3.2.0-rc3-110-g327660f) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5655a6a5f1a7bce768c728e3"),
  "name": "Charmander",
  "description": "A chama que arde na ponta de sua cauda é uma indicação de suas emoções.",
  "type": "fire",
  "attack": 46,
  "heigth": 0.6,
  "defense": 44,
  "moves": [
    "Blaze",
    "Solar Power",
    "desvio"
  ]
}
```

## Pesquisando todos que possuem ataque que eu adicionei

```
mau(mongod-3.2.0-rc3-110-g327660f) be-mean-pokemons> var query = {moves: {$all: ["Overgrow", "Chlorophyll"]}}
mau(mongod-3.2.0-rc3-110-g327660f) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5655a6a5f1a7bce768c728e7"),
  "name": "Bulbasaur",
  "description": "Bulbasaur pode ser visto cochilando sob luz solar intensa",
  "type": "grass",
  "attack": 49,
  "heigth": 0.7,
  "defense": 49,
  "moves": [
    "Overgrow",
    "Chlorophyll",
    "desvio"
  ]
}
Fetched 1 record(s) in 2ms
```

## Pesquisando todos que não são do tipo "elétrico"

```
mau(mongod-3.2.0-rc3-110-g327660f) be-mean-pokemons> var query = {type: {$not: /elétrico/i}}
mau(mongod-3.2.0-rc3-110-g327660f) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5655a6a5f1a7bce768c728e0"),
  "name": "Eevee",
  "description": "Eevee tem uma composição genética instável que de repente se transforma devido ao ambiente em que vive.",
  "type": "normal",
  "attack": 33,
  "heigth": 0.3,
  "defense": 39,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("5655a6a5f1a7bce768c728e1"),
  "name": "Cubone",
  "description": "Vendo a semelhança de sua mãe na lua cheia, ele chora.",
  "type": "ground",
  "attack": 43,
  "heigth": 0.4,
  "defense": 47,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("5655a6a5f1a7bce768c728e2"),
  "name": "Gastly",
  "description": "Gastly é em grande parte é composto de matéria gasosa.",
  "type": "ghost, poison",
  "attack": 50,
  "heigth": 1.3,
  "defense": 51,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("5655a6a5f1a7bce768c728e3"),
  "name": "Charmander",
  "description": "A chama que arde na ponta de sua cauda é uma indicação de suas emoções.",
  "type": "fire",
  "attack": 46,
  "heigth": 0.6,
  "defense": 44,
  "moves": [
    "Blaze",
    "Solar Power",
    "desvio"
  ]
}
{
  "_id": ObjectId("5655a6a5f1a7bce768c728e4"),
  "name": "Mankey",
  "description": "é impossível para qualquer um de fugir a sua ira.",
  "type": "fighting",
  "attack": 48,
  "heigth": 0.5,
  "defense": 45,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("5655a6a5f1a7bce768c728e5"),
  "name": "Pikachu",
  "description": "Sempre que Pikachu se depara para um algo novo, ele ataca com um choque de eletricidade.",
  "type": "eletric",
  "attack": 55,
  "heigth": 0.4,
  "defense": 40,
  "moves": [
    "Static",
    "Lightning Rod",
    "desvio"
  ]
}
{
  "_id": ObjectId("5655a6a5f1a7bce768c728e6"),
  "name": "Squirtle",
  "description": "o casco do Squirtle não é apenas usado para a proteção.",
  "type": "water",
  "attack": 48,
  "heigth": 0.5,
  "defense": 65,
  "moves": [
    "Torrent",
    "Rain Dish",
    "desvio"
  ]
}
{
  "_id": ObjectId("5655a6a5f1a7bce768c728e7"),
  "name": "Bulbasaur",
  "description": "Bulbasaur pode ser visto cochilando sob luz solar intensa",
  "type": "grass",
  "attack": 49,
  "heigth": 0.7,
  "defense": 49,
  "moves": [
    "Overgrow",
    "Chlorophyll",
    "desvio"
  ]
}
{
  "_id": ObjectId("5655a6a5f1a7bce768c728e8"),
  "name": "Shinx",
  "description": "Ele brilha quando está em dificuldades.",
  "type": "electric",
  "attack": 40,
  "heigth": 0.5,
  "defense": 41,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("5655a6a5f1a7bce768c728e9"),
  "name": "Chimchar",
  "description": "Macaco de fogo",
  "type": "fogo",
  "attack": 45,
  "heigth": 0.5,
  "defense": 47,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("5655a6a5f1a7bce768c728ea"),
  "name": "Meowth",
  "description": "este Pokémon ama moedas brilhantes que brilham com a luz.",
  "type": "normal",
  "attack": 43,
  "heigth": 0.4,
  "defense": 41,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("5655a6a5f1a7bce768c728eb"),
  "name": "Aipom",
  "description": "Utiliza sua calda como principal arma.",
  "type": "normal",
  "attack": 39,
  "heigth": 0.8,
  "defense": 38,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("5655a6a5f1a7bce768c728ec"),
  "name": "Drowzee",
  "description": "Comedor de sonhos.",
  "type": "psychic",
  "attack": 46,
  "heigth": 1,
  "defense": 50,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("5655b9bdf1a7bce768c728ed"),
  "name": "AindaNaoExisteMon",
  "attack": null,
  "defense": null,
  "height": null,
  "description": "Sem maiores informações"
}
Fetched 14 record(s) in 13ms
```

## Pesquisando todos que tenham ataque investida E tenham defesa não <= a 49

```
mau(mongod-3.2.0-rc3-110-g327660f) be-mean-pokemons> var query = {$and: [ {moves: {$in: ['investida']}}, {defense: {$not: {$lte: 49}}} ]}
mau(mongod-3.2.0-rc3-110-g327660f) be-mean-pokemons> db.pokemons.find(query)
Fetched 0 record(s) in 1ms
```

## Removendo todos os pokemons do tipo água e com ataque < 50

```
mau(mongod-3.2.0-rc3-110-g327660f) be-mean-pokemons> var query = {$and: [{type: "water"}, {attack: {$lt: 50}}]}
mau(mongod-3.2.0-rc3-110-g327660f) be-mean-pokemons> db.pokemons.remove(query)
Removed 1 record(s) in 5ms
WriteResult({
  "nRemoved": 1
})
```
