#MongoDB - Aula 02 - Exercício
Autor: Sadraque Santos

##Criar database com nome 'be-mean-pokemons'

```
use be-mean-pokemons
switched to db be-mean-pokemons
```

##Listar os databases

```
quasar(mongod-3.2.7) be-mean-pokemons> show dbs
be-mean           → 0.005GB
be-mean-instagram → 0.000GB
be-mean-pokemons  → 0.000GB
local             → 0.000GB
```

##Listar todas as collections

```
quasar(mongod-3.2.7) be-mean-pokemons> show collections
pokemons → 0.001MB / 0.031MB
```

##Criar cinco pokemons

```
var pokelist = [
  {"name": "Charmander",
  "description": "The roof is on fire",
  "attack": "200",
  "defense": "80",
  "height": "0.6" },

  {"name": "Blastoise",
  "description": "They can shoot bullets of water with enough accuracy to strike",
  "attack": "150",
  "defense": "300",
  "height": "1.6" },

  {"name": "Caterpie",
  "description": "Caterpie has a voracious appetite. It can devour leaves bigger than its body right before your eyes. From its antenna, this Pokémon releases a terrifically strong odor.",
  "attack": "25",
  "defense": "60",
  "height": "0.3" },

  {"name": "Jigglypuff",
  "description": "Jigglypuff\"s vocal cords can freely adjust the wavelength of its voice.",
  "attack": "20",
  "defense": "120",
  "height": "0.5" },

  {"name": "Psyduck",
  "description": "Psyduck uses a mysterious power. When it does so, this Pokémon generates brain waves that are supposedly only seen in sleepers",
  "attack": "175",
  "defense": "80",
  "height": "0.8" },

  {"name": "Pikachu",
  "description": "Rato que fala pornografia",
  "attack": "55",
  "defense": "70",
  "height": "0.4"}
]

quasar(mongod-3.2.7) be-mean-pokemons> db.pokemons.insert(pokelist)
Inserted 1 record(s) in 550ms
BulkWriteResult({
  "writeErrors": [ ],
  "writeConcernErrors": [ ],
  "nInserted": 6,
  "nUpserted": 0,
  "nMatched": 0,
  "nModified": 0,
  "nRemoved": 0,
  "upserted": [ ]
})
```

##Listar os pokemons

```
quasar(mongod-3.2.7) be-mean-pokemons> db.pokemons.find()
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
  "_id": ObjectId("578cd7b3d6f8eb39ad6247fc"),
  "name": "Caterpie",
  "description": "Caterpie has a voracious appetite. It can devour leaves bigger than its body right before your eyes. From its antenna, this Pokémon releases a terrifically strong odor.",
  "attack": "25",
  "defense": "60",
  "height": "0.3"
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
{
  "_id": ObjectId("578cd7b3d6f8eb39ad6247ff"),
  "name": "Pikachu",
  "description": "Rato que fala pornografia",
  "attack": "55",
  "defense": "70",
  "height": "0.4"
}
Fetched 6 record(s) in 14ms
```

##Buscar um pokemon

```
quasar(mongod-3.2.7) be-mean-pokemons> db.pokemons.findOne({"name":"Charmander"})
{
  "_id": ObjectId("578cd7b3d6f8eb39ad6247fa"),
  "name": "Charmander",
  "description": "The roof is on fire",
  "attack": "200",
  "defense": "80",
  "height": "0.6"
}
```

##Editar a descrição de um pokemon escolhido

```
quasar(mongod-3.2.7) be-mean-pokemons> var poke = db.pokemons.findOne({"name":"Pikachu"})

quasar(mongod-3.2.7) be-mean-pokemons> poke.description = "Só um rato que dá choque"

quasar(mongod-3.2.7) be-mean-pokemons> db.pokemons.save(poke)
Updated 1 existing record(s) in 28ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})
```
