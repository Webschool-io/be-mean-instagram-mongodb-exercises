#MongoDB - Aula 03 - Exercício
Autor: Sadraque Santos

##Listando todos os pokemons com altura menor que 0.5

```
quasar(mongod-3.2.7) be-mean-pokemons> var query = {"height": {$lt: "0.5"}}
quasar(mongod-3.2.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("578cd7b3d6f8eb39ad6247fc"),
  "name": "Caterpie",
  "description": "Caterpie has a voracious appetite. It can devour leaves bigger than its body right before your eyes. From its antenna, this Pokémon releases a terrifically strong odor.",
  "attack": "25",
  "defense": "60",
  "height": "0.3"
}
{
  "_id": ObjectId("578cd7b3d6f8eb39ad6247ff"),
  "name": "Pikachu",
  "description": "Só um rato que dá choque",
  "attack": "55",
  "defense": "70",
  "height": "0.4"
}
Fetched 2 record(s) in 1ms
```

##Listando todos os pokemons com altura maior ou igual a 0.5

```
quasar(mongod-3.2.7) be-mean-pokemons> var query = {"height": {$gte: "0.5"}}

quasar(mongod-3.2.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("578cd7b3d6f8eb39ad6247fa"),
  "name": "Charmander",
  "description": "The roof is on fire",
  "attack": "200",
  "defense": "80",
  "height": "0.6"
}
{
  "_id": ObjectId("578cd7b3d6f8eb39ad6247fb"),
  "name": "Blastoise",
  "description": "They can shoot bullets of water with enough accuracy to strike",
  "attack": "150",
  "defense": "300",
  "height": "1.6"
}
{
  "_id": ObjectId("578cd7b3d6f8eb39ad6247fd"),
  "name": "Jigglypuff",
  "description": "Jigglypuff\"s vocal cords can freely adjust the wavelength of its voice.",
  "attack": "20",
  "defense": "120",
  "height": "0.5"
}
{
  "_id": ObjectId("578cd7b3d6f8eb39ad6247fe"),
  "name": "Psyduck",
  "description": "Psyduck uses a mysterious power. When it does so, this Pokémon generates brain waves that are supposedly only seen in sleepers",
  "attack": "175",
  "defense": "80",
  "height": "0.8"
}
Fetched 4 record(s) in 1ms
```

##Listando todos os pokemons que rem a altura maior ou igual 0.5 e que são do tipo "grama"

```
quasar(mongod-3.2.7) be-mean-pokemons> var query = {$and: [{"height":{$gte:"0.5"}},{"type": "grama"}]}

quasar(mongod-3.2.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("578cd7b3d6f8eb39ad6247fc"),
  "name": "Caterpie",
  "description": "Caterpie has a voracious appetite. It can devour leaves bigger than its body right before your eyes. From its antenna, this Pokémon releases a terrifically strong odor.",
  "attack": "25",
  "defense": "60",
  "height": "0.6",
  "type": "grama"
}
Fetched 1 record(s) in 1ms
```

##Listando todos os pokemons com nome "Pikachu" ou com attack menor ou igual a 55

```
quasar(mongod-3.2.7) be-mean-pokemons> var query = {$or:
...   [
...   {"name":"Pikachu"},
...   {"attack": {$lte:55}}
...   ]
... }

quasar(mongod-3.2.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("578d2d76a3b0a447e04c8d1f"),
  "name": "Caterpie",
  "description": "Caterpie has a voracious appetite. It can devour leaves bigger than its body right before your eyes. From its antenna, this Pokémon releases a terrifically strong odor",
  "type": "grama",
  "attack": 25,
  "defense": 60,
  "height": 0.3
}
{
  "_id": ObjectId("578d2d76a3b0a447e04c8d20"),
  "name": "Jigglypuff",
  "description": "Jigglypuff\"s vocal cords can freely adjust the wavelength of its voice.",
  "attack": 20,
  "defense": 120,
  "height": 0.5
}
{
  "_id": ObjectId("578d2d76a3b0a447e04c8d22"),
  "name": "Pikachu",
  "description": "Rato que fala pornografia",
  "attack": 55,
  "defense": 70,
  "height": 0.4
}
Fetched 3 record(s) in 1ms
```

##Listando os pokemons com attack maior ou igual a 48 e com altura menor ou igual a 0.5

```
quasar(mongod-3.2.7) be-mean-pokemons> var query = {$and:
...   [
...   {"attack": {$gte: 48}},
...   {"height": {$lte: 0.5}}
...   ]
... }

quasar(mongod-3.2.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("578d2d76a3b0a447e04c8d22"),
  "name": "Pikachu",
  "description": "Rato que fala pornografia",
  "attack": 55,
  "defense": 70,
  "height": 0.4
}
Fetched 1 record(s) in 1ms
```
