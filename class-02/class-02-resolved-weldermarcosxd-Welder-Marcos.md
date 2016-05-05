
# MongoDB - Aula 02 - Exercício
autor: Welder Marcos

## Criação da database  (passo 1)

```
welder@Welder-Mint ~ $ mongo be-mean-pokemons
MongoDB shell version: 3.2.0
connecting to: be-mean-pokemons
Mongo-Hacker 0.0.9
```

## Listagem das databases (passo 2)

```
Welder-Mint(mongod-3.2.0) be-mean-pokemons> show dbs
db     → 0.004GB
local  → 0.000GB
yugioh → 0.000GB
```

## Listagem das coleções (passo 3)

```
Welder-Mint(mongod-3.2.0) be-mean-pokemons> show collections
Welder-Mint(mongod-3.2.0) be-mean-pokemons> 
```

## Cadastro dos pokemons (passo 4)

```
Welder-Mint(mongod-3.2.0) db> var pokemons = [{"name": "Arbok", "description": "Snake", "type": "Poison", "attack": 85, "deffense": 69, "height": 3.5},
... {"name": "Blastoise", "description": "Tortoise", "type": "Water", "attack": 90, "deffense": 150, "height": 1.6},
... {"name": "Venusaur", "description": "Plant", "type": "Grass", "attack": 90, "deffense": 75, "height": 2.0},
... {"name": "Charizard", "description": "Dragon", "type": "Fire", "attack": 90, "deffense": 100, "height": 1.7},
... {"name": "Mew", "description": "Legendary", "type": "Psychic", "attack": 150, "deffense": 100, "height": 0.4},
... {"name": "Wobbuffet", "description": "Figther", "type": "Psychic", "attack": 50, "deffense": 20, "height": 1.3}]

Welder-Mint(mongod-3.2.0) db> pokemons
[
  {
    "name": "Arbok",
    "description": "Snake",
    "type": "Poison",
    "attack": 85,
    "deffense": 69,
    "height": 3.5
  },
  {
    "name": "Blastoise",
    "description": "Tortoise",
    "type": "Water",
    "attack": 90,
    "deffense": 150,
    "height": 1.6
  },
  {
    "name": "Venusaur",
    "description": "Plant",
    "type": "Grass",
    "attack": 90,
    "deffense": 75,
    "height": 2
  },
  {
    "name": "Charizard",
    "description": "Dragon",
    "type": "Fire",
    "attack": 90,
    "deffense": 100,
    "height": 1.7
  },
  {
    "name": "Mew",
    "description": "Legendary",
    "type": "Psychic",
    "attack": 150,
    "deffense": 100,
    "height": 0.4
  },
  {
    "name": "Wobbuffet",
    "description": "Figther",
    "type": "Psychic",
    "attack": 50,
    "deffense": 20,
    "height": 1.3
  }
]

Welder-Mint(mongod-3.2.0) be-mean-pokemons> db.pokemons.insert(pokemons)
Inserted 1 record(s) in 516ms
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

## Lista dos pokemons (passo 5)

```
Welder-Mint(mongod-3.2.0) be-mean-pokemons> var q = db.pokemons
Welder-Mint(mongod-3.2.0) be-mean-pokemons> q.find()
{
  "_id": ObjectId("566c8ed640bc20c0ea5f5920"),
  "name": "Arbok",
  "description": "Snake",
  "type": "Poison",
  "attack": 85,
  "deffense": 69,
  "height": 3.5
}
{
  "_id": ObjectId("566c8ed640bc20c0ea5f5921"),
  "name": "Blastoise",
  "description": "Tortoise",
  "type": "Water",
  "attack": 90,
  "deffense": 150,
  "height": 1.6
}
{
  "_id": ObjectId("566c8ed640bc20c0ea5f5922"),
  "name": "Venusaur",
  "description": "Plant",
  "type": "Grass",
  "attack": 90,
  "deffense": 75,
  "height": 2
}
{
  "_id": ObjectId("566c8ed640bc20c0ea5f5923"),
  "name": "Charizard",
  "description": "Dragon",
  "type": "Fire",
  "attack": 90,
  "deffense": 100,
  "height": 1.7
}
{
  "_id": ObjectId("566c8ed640bc20c0ea5f5924"),
  "name": "Mew",
  "description": "Legendary",
  "type": "Psychic",
  "attack": 150,
  "deffense": 100,
  "height": 0.4
}
{
  "_id": ObjectId("566c8ed640bc20c0ea5f5925"),
  "name": "Wobbuffet",
  "description": "Figther",
  "type": "Psychic",
  "attack": 50,
  "deffense": 20,
  "height": 1.3
}
Fetched 6 record(s) in 3ms
```

## Pokemon (passo 6)

```
Welder-Mint(mongod-3.2.0) be-mean-pokemons> var q = {name: "Mew"}
Welder-Mint(mongod-3.2.0) be-mean-pokemons> var d = db.pokemons
Welder-Mint(mongod-3.2.0) be-mean-pokemons> d.find(q)
{
  "_id": ObjectId("566c8ed640bc20c0ea5f5924"),
  "name": "Mew",
  "description": "Legendary",
  "type": "Psychic",
  "attack": 150,
  "deffense": 100,
  "height": 0.4
}
Fetched 1 record(s) in 3ms
```

## Atualização do Pokemon (passo 7)

```
Welder-Mint(mongod-3.2.0) be-mean-pokemons> var q = {name: "Wobbuffet"}
Welder-Mint(mongod-3.2.0) be-mean-pokemons> q
{
  "name": "Wobbuffet"
}
Welder-Mint(mongod-3.2.0) be-mean-pokemons> var poke = d.findOne(q)
Welder-Mint(mongod-3.2.0) be-mean-pokemons> poke
{
  "_id": ObjectId("566c8ed640bc20c0ea5f5925"),
  "name": "Wobbuffet",
  "description": "Figther",
  "type": "Psychic",
  "attack": 50,
  "deffense": 20,
  "height": 1.3
}

Welder-Mint(mongod-3.2.0) be-mean-pokemons> poke.description
Figther
Welder-Mint(mongod-3.2.0) be-mean-pokemons> poke.description = "Zueiro do Anime"
Zueiro do Anime
Welder-Mint(mongod-3.2.0) be-mean-pokemons> d.save(poke)
Updated 1 existing record(s) in 1ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})
Welder-Mint(mongod-3.2.0) be-mean-pokemons> d.findOne(q)
{
  "_id": ObjectId("566c8ed640bc20c0ea5f5925"),
  "name": "Wobbuffet",
  "description": "Zueiro do Anime",
  "type": "Psychic",
  "attack": 50,
  "deffense": 20,
  "height": 1.3
}
```

