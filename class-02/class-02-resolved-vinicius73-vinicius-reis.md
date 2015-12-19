
# MongoDB - Aula 02 - Exercício
autor: Vinicius Reis

## Listagem das databases (passo 2)

```
zaraki(mongod-3.0.7) test> use be-mean-pokemons
switched to db be-mean-pokemons
zaraki(mongod-3.0.7) be-mean-pokemons> show dbs
local   → 0.078GB
be-mean → 0.078GB
test    → 0.078GB
zaraki(mongod-3.0.7) be-mean-pokemons>
```

## Listagem das coleções (passo 3)

```
zaraki(mongod-3.0.7) be-mean-pokemons> show collections
zaraki(mongod-3.0.7) be-mean-pokemons>
```

## Cadastro dos pokemons (passo 4)

```
zaraki(mongod-3.0.7) be-mean-pokemons> var pokemons = [{name: 'Suissamon', description: 'Pokemon Hacker', type: 'hacker', attack: 8001, defense: 8000, height: 1.69},{name: 'Dilmamon', description: 'Pokemon presidANTA', type: 'besta', attack: 1, defense: 1, height: 1.60},{name: 'Cunhamon', description: 'Filho da rapiga', type: 'besta', attack: 9990, defense: 9999, height: 1.80},{name: 'Calheirosmon', description: 'Irmão do filho da rapiga', type: 'besta', attack: 8500, defense: 9999, height: 1.79},{name: 'FeliciANUS', description: 'Pastor...', type: 'besta', attack: 666, defense: 666, height: 1.70}]
zaraki(mongod-3.0.7) be-mean-pokemons> pokemons
[
  {
    "name": "Suissamon",
    "description": "Pokemon Hacker",
    "type": "hacker",
    "attack": 8001,
    "defense": 8000,
    "height": 1.69
  },
  {
    "name": "Dilmamon",
    "description": "Pokemon presidANTA",
    "type": "besta",
    "attack": 1,
    "defense": 1,
    "height": 1.6
  },
  {
    "name": "Cunhamon",
    "description": "Filho da rapiga",
    "type": "besta",
    "attack": 9990,
    "defense": 9999,
    "height": 1.8
  },
  {
    "name": "Calheirosmon",
    "description": "Irmão do filho da rapiga",
    "type": "besta",
    "attack": 8500,
    "defense": 9999,
    "height": 1.79
  },
  {
    "name": "FeliciANUS",
    "description": "Pastor...",
    "type": "besta",
    "attack": 666,
    "defense": 666,
    "height": 1.7
  }
]
zaraki(mongod-3.0.7) be-mean-pokemons> db.pokemons.insert(pokemons)
Inserted 1 record(s) in 85ms
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
zaraki(mongod-3.0.7) be-mean-pokemons>
```

## Lista dos pokemons (passo 5)

```
zaraki(mongod-3.0.7) be-mean-pokemons> db.pokemons.find()
{
  "_id": ObjectId("56507b416f97e66bd9f5d6fd"),
  "name": "Suissamon",
  "description": "Pokemon Hacker",
  "type": "hacker",
  "attack": 8001,
  "defense": 8000,
  "height": 1.69
}
{
  "_id": ObjectId("56507b416f97e66bd9f5d6fe"),
  "name": "Dilmamon",
  "description": "Pokemon presidANTA",
  "type": "besta",
  "attack": 1,
  "defense": 1,
  "height": 1.6
}
{
  "_id": ObjectId("56507b416f97e66bd9f5d6ff"),
  "name": "Cunhamon",
  "description": "Filho da rapiga",
  "type": "besta",
  "attack": 9990,
  "defense": 9999,
  "height": 1.8
}
{
  "_id": ObjectId("56507b416f97e66bd9f5d700"),
  "name": "Calheirosmon",
  "description": "Irmão do filho da rapiga",
  "type": "besta",
  "attack": 8500,
  "defense": 9999,
  "height": 1.79
}
{
  "_id": ObjectId("56507b416f97e66bd9f5d701"),
  "name": "FeliciANUS",
  "description": "Pastor...",
  "type": "besta",
  "attack": 666,
  "defense": 666,
  "height": 1.7
}
Fetched 5 record(s) in 7ms
zaraki(mongod-3.0.7) be-mean-pokemons>
```

## Pokemon (passo 6)

```
zaraki(mongod-3.0.7) be-mean-pokemons>  var query = {"name": "Suissamon"}
zaraki(mongod-3.0.7) be-mean-pokemons> var poke = db.pokemons.findOne(query)
zaraki(mongod-3.0.7) be-mean-pokemons> poke
{
  "_id": ObjectId("56507b416f97e66bd9f5d6fd"),
  "name": "Suissamon",
  "description": "Pokemon Hacker",
  "type": "hacker",
  "attack": 8001,
  "defense": 8000,
  "height": 1.69
}
zaraki(mongod-3.0.7) be-mean-pokemons>
```

## Atualização do Pokemon (passo 7)

```
zaraki(mongod-3.0.7) be-mean-pokemons>  var query = {"name": "Suissamon"}
zaraki(mongod-3.0.7) be-mean-pokemons> var poke = db.pokemons.findOne(query)
zaraki(mongod-3.0.7) be-mean-pokemons> poke
{
  "_id": ObjectId("56507b416f97e66bd9f5d6fd"),
  "name": "Suissamon",
  "description": "Pokemon Hacker",
  "type": "hacker",
  "attack": 8001,
  "defense": 8000,
  "height": 1.69
}
zaraki(mongod-3.0.7) be-mean-pokemons> poke.description
Pokemon Hacker
zaraki(mongod-3.0.7) be-mean-pokemons> poke.description = "Loko mais legal"
Loko mais legal
zaraki(mongod-3.0.7) be-mean-pokemons> db.pokemons.save(poke)
Updated 1 existing record(s) in 20ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})
zaraki(mongod-3.0.7) be-mean-pokemons> db.pokemons.findOne(query)
{
  "_id": ObjectId("56507b416f97e66bd9f5d6fd"),
  "name": "Suissamon",
  "description": "Loko mais legal",
  "type": "hacker",
  "attack": 8001,
  "defense": 8000,
  "height": 1.69
}
zaraki(mongod-3.0.7) be-mean-pokemons>
```
