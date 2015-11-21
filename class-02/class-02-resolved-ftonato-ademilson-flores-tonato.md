# MongoDB - Aula 02 - Exercício
autor: Ademílson F. Tonato

## Listagem das databases (passo 2)
```
lucasft(mongod-2.6.10) use be-mean-pokemons
switched to db be-mean-pokemons

lucasft(mongod-2.6.10) be-mean-pokemons> show dbs
teste              0.078GB
be-mean            0.078GB
test               0.078GB
local              0.078GB
be-mean-instagram  0.078GB
admin              (empty)
```

## Listagem das coleções (passo 3)

```
lucasft(mongod-2.6.10) be-mean-pokemons> show collections
lucasft(mongod-2.6.10) be-mean-pokemons> 
```

## Cadastro dos pokemons (passo 4)

```
lucasft(mongod-2.6.10) be-mean-pokemons> show collections
lucasft(mongod-2.6.10) be-mean-pokemons> var pokemons = [{name: 'A', description: 'Aa', type: 'Tipo A', attack: 100, defense: 100, height: 1.00},{name: 'B', description: 'Bb', type: 'Tipo B', attack: 200, defense: 1, height: 1.88},{name: 'C', description: 'Cc', type: 'Tipo C', attack: 30, defense: 9999, height: 1.09},{name: 'D', description: 'Dd', type: 'Tipo d', attack: 88, defense: 123, height: 1.83},{name: 'Tio Bill', description: 'O dono do pior sistema operacional do mundo', type: 'Desenvolvedor', attack: 1, defense: 666, height: 1.11}]
lucasft(mongod-2.6.10) be-mean-pokemons> pokemons
[
  {
    "name": "A",
    "description": "Aa",
    "type": "Tipo A",
    "attack": 100,
    "defense": 100,
    "height": 1
  },
  {
    "name": "B",
    "description": "Bb",
    "type": "Tipo B",
    "attack": 200,
    "defense": 1,
    "height": 1.88
  },
  {
    "name": "C",
    "description": "Cc",
    "type": "Tipo C",
    "attack": 30,
    "defense": 9999,
    "height": 1.09
  },
  {
    "name": "D",
    "description": "Dd",
    "type": "Tipo d",
    "attack": 88,
    "defense": 123,
    "height": 1.83
  },
  {
    "name": "Tio Bill",
    "description": "O dono do pior sistema operacional do mundo",
    "type": "Desenvolvedor",
    "attack": 1,
    "defense": 666,
    "height": 1.11
  }
]
lucasft(mongod-2.6.10) be-mean-pokemons> db.pokemons.insert(pokemons)
Inserted 1 record(s) in 603ms
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
lucasft(mongod-2.6.10) be-mean-pokemons> db.pokemons.find()
{
  "_id": ObjectId("5650de238dc00a07eadf94c3"),
  "name": "A",
  "description": "Aa",
  "type": "Tipo A",
  "attack": 100,
  "defense": 100,
  "height": 1
}
{
  "_id": ObjectId("5650de238dc00a07eadf94c4"),
  "name": "B",
  "description": "Bb",
  "type": "Tipo B",
  "attack": 200,
  "defense": 1,
  "height": 1.88
}
{
  "_id": ObjectId("5650de238dc00a07eadf94c5"),
  "name": "C",
  "description": "Cc",
  "type": "Tipo C",
  "attack": 30,
  "defense": 9999,
  "height": 1.09
}
{
  "_id": ObjectId("5650de238dc00a07eadf94c6"),
  "name": "D",
  "description": "Dd",
  "type": "Tipo d",
  "attack": 88,
  "defense": 123,
  "height": 1.83
}
{
  "_id": ObjectId("5650de238dc00a07eadf94c7"),
  "name": "Tio Bill",
  "description": "O dono do pior sistema operacional do mundo",
  "type": "Desenvolvedor",
  "attack": 1,
  "defense": 666,
  "height": 1.11
}
Fetched 5 record(s) in 2ms
```

## Pikachu (passo 6)

```
lucasft(mongod-2.6.10) be-mean-pokemons> var query = {"name": "C"}
lucasft(mongod-2.6.10) be-mean-pokemons> var poke = db.pokemons.findOne(query)
lucasft(mongod-2.6.10) be-mean-pokemons> poke
{
  "_id": ObjectId("5650de238dc00a07eadf94c5"),
  "name": "C",
  "description": "Cc",
  "type": "Tipo C",
  "attack": 30,
  "defense": 9999,
  "height": 1.09
}

```

## Atualização do Pikachu (passo 7)

```
lucasft(mongod-2.6.10) be-mean-pokemons> var query = {"name": "C"}
lucasft(mongod-2.6.10) be-mean-pokemons> var poke = db.pokemons.findOne(query)
lucasft(mongod-2.6.10) be-mean-pokemons> poke.description
Cc
lucasft(mongod-2.6.10) be-mean-pokemons> poke.description = 'A descrição foi alterada :)'
A descrição foi alterada :)
lucasft(mongod-2.6.10) be-mean-pokemons> db.pokemons.save(poke)
Updated 1 existing record(s) in 2ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})
lucasft(mongod-2.6.10) be-mean-pokemons> db.pokemons.findOne(query)
{
  "_id": ObjectId("5650de238dc00a07eadf94c5"),
  "name": "C",
  "description": "A descrição foi alterada :)",
  "type": "Tipo C",
  "attack": 30,
  "defense": 9999,
  "height": 1.09
}
```