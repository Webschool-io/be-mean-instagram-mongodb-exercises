# MongoDB - Aula 01 - Exercício
autor: Pedro Henrique Prado Oliveira

## Listagem das databases (passo 2)

```
use be-mean-pokemons
switched to db be-mean-pokemons
show dbs
be-mean-instagram → 0.078GB
be-mean           → 0.078GB
dbCursoMongoDb    → 0.078GB
local             → 0.078GB
```

## Listagem das coleções (passo 3)

```
show collections
```

## Cadastro dos pokemons (passo 4)
```
registroPokemons
[
  {
    "name": "Charizard",
    "description": "Fire",
    "attack": 84,
    "defense": 78,
    "height": 1.7
  },
  {
    "name": "Pikachu",
    "description": "Eletric",
    "attack": 30,
    "defense": 20,
    "height": 0.4
  },
  {
    "name": "Mewtwo",
    "description": "Psychic",
    "attack": 110,
    "defense": 90,
    "height": 2
  },
  {
    "name": "Gyarados",
    "description": "Water",
    "attack": 125,
    "defense": 70,
    "height": 6.5
  },
  {
    "name": "Blastoise",
    "description": "Water",
    "attack": 83,
    "defense": 100,
    "height": 1.6
  }
]

db.pokemons.insert(registroPokemons)
Inserted 1 record(s) in 3ms
BulkWriteResult({
  "writeErrors": [ ],
  "writeConcernErrors": [ ],
  "nInserted": 5,
  "nUpserted": 0,
  "nMatched": 0,
  "nModified": 0,
  "nRemoved": 0,
  "upserted": [ ]
})

```

## Lista dos pokemons (passo 5)
```
db.pokemons.find()
{
  "_id": ObjectId("564ca8b56ddc0f98523dd507"),
  "name": "Charizard",
  "description": "Fire",
  "attack": 84,
  "defense": 78,
  "height": 1.7
}
{
  "_id": ObjectId("564ca8b56ddc0f98523dd508"),
  "name": "Pikachu",
  "description": "Eletric",
  "attack": 30,
  "defense": 20,
  "height": 0.4
}
{
  "_id": ObjectId("564ca8b56ddc0f98523dd509"),
  "name": "Mewtwo",
  "description": "Psychic",
  "attack": 110,
  "defense": 90,
  "height": 2
}
{
  "_id": ObjectId("564ca8b56ddc0f98523dd50a"),
  "name": "Gyarados",
  "description": "Water",
  "attack": 125,
  "defense": 70,
  "height": 6.5
}
{
  "_id": ObjectId("564ca8b56ddc0f98523dd50b"),
  "name": "Blastoise",
  "description": "Water",
  "attack": 83,
  "defense": 100,
  "height": 1.6
}
Fetched 5 record(s) in 1ms
```
## Buscar um pokemon e amazenar na variável poke (passo 6)
```
var query = {name: "Mewtwo"}
var poke = db.pokemons.findOne(query)
poke
{
  "_id": ObjectId("564ca8b56ddc0f98523dd509"),
  "name": "Mewtwo",
  "description": "Psychic",
  "attack": 110,
  "defense": 90,
  "height": 2
}
```
## Atualização do pokemon (passo 7)
```
poke.description
Psychic
poke.description = "Pokemon fodão"
Pokemon fodão
db.pokemons.save(poke)
Updated 1 existing record(s) in 98ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})
```
