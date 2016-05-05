
# MongoDB - Aula 02 - Exercício
autor: Bruno Rodrigues

## Listagem das databases (passo 2)

```
bruno-dev(mongod-3.0.7) be-mean-instagram> use be-mean-pokemons
switched to db be-mean-pokemons


bruno-dev(mongod-3.0.7) be-mean-pokemons> show dbs
be-mean-teste      0.078GB
be-mean-instagram  0.078GB
be-mean            0.078GB
local              0.078GB

```

## Listagem das coleções (passo 3)

```
bruno-dev(mongod-3.0.7) be-mean-pokemons> show collections
bruno-dev(mongod-3.0.7) be-mean-pokemons>
```

## Cadastro dos pokemons (passo 4)

```
bruno-dev(mongod-3.0.7) be-mean-pokemons> var pokemons = [{name:'Watchog', description:'Using luminescent matter, it makes its eyes and body glow and stuns attacking opponents.', attack: 85 , defense: 69 , height: 11 },{name:'Metapod', description:'The shell covering this Pokémons body is as hard as an iron slab', attack: 20, defense: 55, height: 7},{name:'Vulpix', description:'At the time of its birth, Vulpix has one white tail.', attack: 41, defense: 40, height: 6 },{name:'PsyDuck', description:'Psyduck uses a mysterious power.', attack: 52, defense: 48, height: 8 },{name:'Machop', description:'Machops muscles are special—they never get sore no matter how much they are used in exercise.', attack: 88, defense: 50, height: 8 }]

bruno-dev(mongod-3.0.7) be-mean-pokemons> pokemons
[
  {
    "name": "Watchog",
    "description": "Using luminescent matter, it makes its eyes and body glow and stuns attacking opponents.",
    "attack": 85,
    "defense": 69,
    "height": 11
  },
  {
    "name": "Metapod",
    "description": "The shell covering this Pokémons body is as hard as an iron slab",
    "attack": 20,
    "defense": 55,
    "height": 7
  },
  {
    "name": "Vulpix",
    "description": "At the time of its birth, Vulpix has one white tail.",
    "attack": 41,
    "defense": 40,
    "height": 6
  },
  {
    "name": "PsyDuck",
    "description": "Psyduck uses a mysterious power.",
    "attack": 52,
    "defense": 48,
    "height": 8
  },
  {
    "name": "Machop",
    "description": "Machops muscles are special—they never get sore no matter how much they are used in exercise.",
    "attack": 88,
    "defense": 50,
    "height": 8
  }
]

bruno-dev(mongod-3.0.7) be-mean-pokemons> db.pokemons.insert(pokemons)
Inserted 1 record(s) in 66ms
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

bruno-dev(mongod-3.0.7) be-mean-pokemons> db.pokemons.find()
{
  "_id": ObjectId("565a351d003ef3cf967e2628"),
  "name": "Watchog",
  "description": "Using luminescent matter, it makes its eyes and body glow and stuns attacking opponents.",
  "attack": 85,
  "defense": 69,
  "height": 11
}
{
  "_id": ObjectId("565a351d003ef3cf967e2629"),
  "name": "Metapod",
  "description": "The shell covering this Pokémons body is as hard as an iron slab",
  "attack": 20,
  "defense": 55,
  "height": 7
}
{
  "_id": ObjectId("565a351d003ef3cf967e262a"),
  "name": "Vulpix",
  "description": "At the time of its birth, Vulpix has one white tail.",
  "attack": 41,
  "defense": 40,
  "height": 6
}
{
  "_id": ObjectId("565a351d003ef3cf967e262b"),
  "name": "PsyDuck",
  "description": "Psyduck uses a mysterious power.",
  "attack": 52,
  "defense": 48,
  "height": 8
}
{
  "_id": ObjectId("565a351d003ef3cf967e262c"),
  "name": "Machop",
  "description": "Machops muscles are special—they never get sore no matter how much they are used in exercise.",
  "attack": 88,
  "defense": 50,
  "height": 8
}
Fetched 5 record(s) in 2ms

```

## Pokemon (passo 6)

```
bruno-dev(mongod-3.0.7) be-mean-pokemons> var query = {"name": "PsyDuck"}
bruno-dev(mongod-3.0.7) be-mean-pokemons> var poke = db.pokemons.findOne(query)
bruno-dev(mongod-3.0.7) be-mean-pokemons> poke
{
  "_id": ObjectId("565a351d003ef3cf967e262b"),
  "name": "PsyDuck",
  "description": "Psyduck uses a mysterious power.",
  "attack": 52,
  "defense": 48,
  "height": 8
}


```

## Atualização do Pokemon (passo 7)

```
bruno-dev(mongod-3.0.7) be-mean-pokemons> poke.description
Psyduck uses a mysterious power.
bruno-dev(mongod-3.0.7) be-mean-pokemons> poke.description = "Boneco maluco"
Boneco maluco
bruno-dev(mongod-3.0.7) be-mean-pokemons> db.pokemons.save(poke)
Updated 1 existing record(s) in 1ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})
bruno-dev(mongod-3.0.7) be-mean-pokemons> db.pokemons.findOne(query)
{
  "_id": ObjectId("565a351d003ef3cf967e262b"),
  "name": "PsyDuck",
  "description": "Boneco maluco",
  "attack": 52,
  "defense": 48,
  "height": 8
}


```
