# MongoDB - Aula 02 - Exercício
autor: JEAN PAULO AMARAL

## Listagem das databases (passo 2)
```
scotchbox(mongod-3.0.7) be-mean-pokemons> use be-mean-pokemons
switched to db be-mean-pokemons

scotchbox(mongod-3.0.7) be-mean-pokemons> show dbs
be-mean-instagram → 0.078GB
be-mean           → 0.078GB
scotchbox         → 0.078GB
local             → 0.078GB
```

## Listagem das coleções (passo 3)
```
scotchbox(mongod-3.0.7) test> show collections
```

## Cadastro dos pokemons (passo 4)
```
scotchbox(mongod-3.0.7) test> var pokemons =
... [
...   { 'name': 'Pidgey', 'description': 'Pombinho maroto', 'type': 'Normal/Flying', attack: 45, height: 1, defense: 40 } ,
...   { 'name': 'Ekans', 'description': 'Cobra do mal', 'type': 'Poison', attack: 60, height: 6, defense: 44 } ,
...   { 'name': 'Tauros', 'description': 'Touro Espanhol', 'type': 'Normal', attack: 100, height: 4, defense: 95 } ,
...   { 'name': 'Pinsir', 'description': 'Corta grama', 'type': 'Bug', attack: 125, height: 4, defense: 100 } ,
...   { 'name': 'Lapras', 'description': 'Nada e Nada', 'type': 'Water', attack: 85, height: 8, defense: 80 } ,
...   { 'name': 'Sentret', 'description': 'Furão doido', 'type': 'Normal', attack: 46, height: 2, defense: 34 } ,
...   { 'name': 'Poliwhirl', 'description': 'Treco estranho do mar', 'type': 'Water', attack: 65, height: 3, defense: 65 } ,
...   { 'name': 'Togepi', 'description': 'Treco chato', 'type': 'Fairy', attack: 20, height: 1, defense: 65 }
... ]
scotchbox(mongod-3.0.7) test> pokemons
[
  {
    "name": "Pidgey",
    "description": "Pombinho maroto",
    "type": "Normal/Flying",
    "attack": 45,
    "height": 1,
    "defense": 40
  },
  {
    "name": "Ekans",
    "description": "Cobra do mal",
    "type": "Poison",
    "attack": 60,
    "height": 6,
    "defense": 44
  },
  {
    "name": "Tauros",
    "description": "Touro Espanhol",
    "type": "Normal",
    "attack": 100,
    "height": 4,
    "defense": 95
  },
  {
    "name": "Pinsir",
    "description": "Corta grama",
    "type": "Bug",
    "attack": 125,
    "height": 4,
    "defense": 100
  },
  {
    "name": "Lapras",
    "description": "Nada e Nada",
    "type": "Water",
    "attack": 85,
    "height": 8,
    "defense": 80
  },
  {
    "name": "Sentret",
    "description": "Furão doido",
    "type": "Normal",
    "attack": 46,
    "height": 2,
    "defense": 34
  },
  {
    "name": "Poliwhirl",
    "description": "Treco estranho do mar",
    "type": "Water",
    "attack": 65,
    "height": 3,
    "defense": 65
  },
  {
    "name": "Togepi",
    "description": "Treco chato",
    "type": "Fairy",
    "attack": 20,
    "height": 1,
    "defense": 65
  }
]
```
```
scotchbox(mongod-3.0.7) test> db.pokemons.insert(pokemons)
Inserted 1 record(s) in 38ms
BulkWriteResult({
  "writeErrors": [ ],
  "writeConcernErrors": [ ],
  "nInserted": 8,
  "nUpserted": 0,
  "nMatched": 0,
  "nModified": 0,
  "nRemoved": 0,
  "upserted": [ ]
})
```

## Lista dos pokemons (passo 5)
```
scotchbox(mongod-3.0.7) test> db.pokemons.find()
{
  "_id": ObjectId("565a368d8675ae8a0db23290"),
  "name": "Pidgey",
  "description": "Pombinho maroto",
  "type": "Normal/Flying",
  "attack": 45,
  "height": 1,
  "defense": 40
}
{
  "_id": ObjectId("565a368d8675ae8a0db23291"),
  "name": "Ekans",
  "description": "Cobra do mal",
  "type": "Poison",
  "attack": 60,
  "height": 6,
  "defense": 44
}
{
  "_id": ObjectId("565a368d8675ae8a0db23292"),
  "name": "Tauros",
  "description": "Touro Espanhol",
  "type": "Normal",
  "attack": 100,
  "height": 4,
  "defense": 95
}
{
  "_id": ObjectId("565a368d8675ae8a0db23293"),
  "name": "Pinsir",
  "description": "Corta grama",
  "type": "Bug",
  "attack": 125,
  "height": 4,
  "defense": 100
}
{
  "_id": ObjectId("565a368d8675ae8a0db23294"),
  "name": "Lapras",
  "description": "Nada e Nada",
  "type": "Water",
  "attack": 85,
  "height": 8,
  "defense": 80
}
{
  "_id": ObjectId("565a368d8675ae8a0db23295"),
  "name": "Sentret",
  "description": "Furão doido",
  "type": "Normal",
  "attack": 46,
  "height": 2,
  "defense": 34
}
{
  "_id": ObjectId("565a368d8675ae8a0db23296"),
  "name": "Poliwhirl",
  "description": "Treco estranho do mar",
  "type": "Water",
  "attack": 65,
  "height": 3,
  "defense": 65
}
{
  "_id": ObjectId("565a368d8675ae8a0db23297"),
  "name": "Togepi",
  "description": "Treco chato",
  "type": "Fairy",
  "attack": 20,
  "height": 1,
  "defense": 65
}
Fetched 8 record(s) in 12ms

```

## Procurando Pokemon Pinsir (Passo 6)
```
scotchbox(mongod-3.0.7) test> var query = {"name": "Pinsir"}
scotchbox(mongod-3.0.7) test> query
{
  "name": "Pinsir"
}
scotchbox(mongod-3.0.7) test> db.pokemons.findOne(query)
{
  "_id": ObjectId("565a368d8675ae8a0db23293"),
  "name": "Pinsir",
  "description": "Corta grama",
  "type": "Bug",
  "attack": 125,
  "height": 4,
  "defense": 100
}
```
```
scotchbox(mongod-3.0.7) test> var query = {"name": "Pinsir"}
scotchbox(mongod-3.0.7) test> query
{
  "name": "Pinsir"
}
scotchbox(mongod-3.0.7) test> var poke = db.pokemons.findOne(query)
scotchbox(mongod-3.0.7) test> poke
{
  "_id": ObjectId("565a368d8675ae8a0db23293"),
  "name": "Pinsir",
  "description": "Corta grama",
  "type": "Bug",
  "attack": 125,
  "height": 4,
  "defense": 100
}
```

## Atualização do Pokemon (passo 7)
```
scotchbox(mongod-3.0.7) test> poke.description
Corta grama
scotchbox(mongod-3.0.7) test> poke.description = 'Pokemon loucão que corta tudo'
Pokemon loucão que corta tudo
scotchbox(mongod-3.0.7) test> db.pokemons.save(poke)
Updated 1 existing record(s) in 2ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})
```
```
scotchbox(mongod-3.0.7) test> db.pokemons.findOne(query)
{
  "_id": ObjectId("565a368d8675ae8a0db23293"),
  "name": "Pinsir",
  "description": "Pokemon loucão que corta tudo",
  "type": "Bug",
  "attack": 125,
  "height": 4,
  "defense": 100
}
```