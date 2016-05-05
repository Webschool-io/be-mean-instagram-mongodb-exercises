
# MongoDB - Aula 02 - Exercício
autor: Michel Mattos

## Listagem das databases (passo 2)

```
test> use be-mean-pokemons
switched to db be-mean-pokemons

be-mean-pokemons> show dbs
be-mean-instagram → 0.078GB
be-mean           → 0.078GB
contatooh         → 0.078GB
local             → 0.078GB
admin             → (empty)
```

## Listagem das coleções (passo 3)

```
be-mean-pokemons> show collections
<<<<<<< HEAD
=======
system.indexes → 0.000MB / 0.008MB
>>>>>>> a7bb32d06f1c3ef509b546835f834d7c65a32a9b
```

## Cadastro dos pokemons (passo 4)

```
be-mean-pokemons> var pokemons = [{ "name" : "Nidoqueen", "description" : "Its hard scales provide strong protection. It uses its hefty bulk to execute powerful moves.", "type" : [ "poison", "ground" ], "attack" : 92, "height" : 13, "defense" : 87 },{ "name" : "Mankey", "description" : "Extremely quick to anger. It could be docile one moment then thrashing away the next instant.", "type" : [ "fighting" ], "attack" : 80, "height" : 5, "defense" : 35 },{ "name" : "Sewaddle", "description" : "Leavanny dress it in clothes they made for it when it hatched. It hides its head in its hood while it is sleeping.", "type" : [ "bug", "grass" ], "attack" : 53, "height" : 3, "defense" : 70 },{ "name" : "Wigglytuff", "description" : "The body is soft and rubbery. When angered, it will suck in air and inflate itself to an enormous size.", "type" : [ "normal", "fairy" ], "attack" : 70, "height" : 10, "defense" : 45 },{ "name" : "Gyarados", "description" : "It has an extremely aggressive nature. The HYPER BEAM it shoots from its mouth totally incinerates all targets.", "type" : [ "flying", "water" ], "attack" : 125, "height" : 65, "defense" : 79 }]
be-mean-pokemons> pokemons
[
  {
    "name": "Nidoqueen",
    "description": "Its hard scales provide strong protection. It uses its hefty bulk to execute powerful moves.",
    "type": [
      "poison",
      "ground"
    ],
    "attack": 92,
    "height": 13,
    "defense": 87
  },
  {
    "name": "Mankey",
    "description": "Extremely quick to anger. It could be docile one moment then thrashing away the next instant.",
    "type": [
      "fighting"
    ],
    "attack": 80,
    "height": 5,
    "defense": 35
  },
  {
    "name": "Sewaddle",
    "description": "Leavanny dress it in clothes they made for it when it hatched. It hides its head in its hood while it is sleeping.",
    "type": [
      "bug",
      "grass"
    ],
    "attack": 53,
    "height": 3,
    "defense": 70
  },
  {
    "name": "Wigglytuff",
    "description": "The body is soft and rubbery. When angered, it will suck in air and inflate itself to an enormous size.",
    "type": [
      "normal",
      "fairy"
    ],
    "attack": 70,
    "height": 10,
    "defense": 45
  },
  {
    "name": "Gyarados",
    "description": "It has an extremely aggressive nature. The HYPER BEAM it shoots from its mouth totally incinerates all targets.",
    "type": [
      "flying",
      "water"
    ],
    "attack": 125,
    "height": 65,
    "defense": 79
  }
]
be-mean-pokemons> db.pokemons.insert(pokemons)
Inserted 1 record(s) in 4ms
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
be-mean-pokemons> db.pokemons.find()
{
  "_id": ObjectId("56489de98127ab809fa71573"),
  "name": "Nidoqueen",
  "description": "Its hard scales provide strong protection. It uses its hefty bulk to execute powerful moves.",
  "type": [
    "poison",
    "ground"
  ],
  "attack": 92,
  "height": 13,
  "defense": 87
}
{
  "_id": ObjectId("56489de98127ab809fa71574"),
  "name": "Mankey",
  "description": "Extremely quick to anger. It could be docile one moment then thrashing away the next instant.",
  "type": [
    "fighting"
  ],
  "attack": 80,
  "height": 5,
  "defense": 35
}
{
  "_id": ObjectId("56489de98127ab809fa71575"),
  "name": "Sewaddle",
  "description": "Leavanny dress it in clothes they made for it when it hatched. It hides its head in its hood while it is sleeping.",
  "type": [
    "bug",
    "grass"
  ],
  "attack": 53,
  "height": 3,
  "defense": 70
}
{
  "_id": ObjectId("56489de98127ab809fa71576"),
  "name": "Wigglytuff",
  "description": "The body is soft and rubbery. When angered, it will suck in air and inflate itself to an enormous size.",
  "type": [
    "normal",
    "fairy"
  ],
  "attack": 70,
  "height": 10,
  "defense": 45
}
{
  "_id": ObjectId("56489de98127ab809fa71577"),
  "name": "Gyarados",
  "description": "It has an extremely aggressive nature. The HYPER BEAM it shoots from its mouth totally incinerates all targets.",
  "type": [
    "flying",
    "water"
  ],
  "attack": 125,
  "height": 65,
  "defense": 79
}
Fetched 5 record(s) in 11ms
```

## Gyarados (passo 6)

```
be-mean-pokemons> var q = { name: 'Gyarados' }
be-mean-pokemons> var poke = db.pokemons.findOne(q)
be-mean-pokemons> poke
{
  "_id": ObjectId("56489de98127ab809fa71577"),
  "name": "Gyarados",
  "description": "It has an extremely aggressive nature. The HYPER BEAM it shoots from its mouth totally incinerates all targets.",
  "type": [
    "flying",
    "water"
  ],
  "attack": 125,
  "height": 65,
  "defense": 79
}
```

## Atualização do Gyarados (passo 7)

```
be-mean-pokemons> poke.description
It has an extremely aggressive nature. The HYPER BEAM it shoots from its mouth totally incinerates all targets.

be-mean-pokemons> poke.description = 'Se der o comando "meia-lua-pra-frente-e-soco" o Gyarados soltará um HADOUKEN!!!'
Se der o comando "meia-lua-pra-frente-e-soco" o Gyarados soltará um HADOUKEN!!!

be-mean-pokemons> poke
{
  "_id": ObjectId("56489de98127ab809fa71577"),
  "name": "Gyarados",
  "description": "Se der o comando \"meia-lua-pra-frente-e-soco\" o Gyarados soltará um HADOUKEN!!!",
  "type": [
    "flying",
    "water"
  ],
  "attack": 125,
  "height": 65,
  "defense": 79
}

be-mean-pokemons> db.pokemons.save(poke)
Updated 1 existing record(s) in 3ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})

be-mean-pokemons> db.pokemons.findOne(q)
{
  "_id": ObjectId("56489de98127ab809fa71577"),
  "name": "Gyarados",
  "description": "Se der o comando \"meia-lua-pra-frente-e-soco\" o Gyarados soltará um HADOUKEN!!!",
  "type": [
    "flying",
    "water"
  ],
  "attack": 125,
  "height": 65,
  "defense": 79
}
```