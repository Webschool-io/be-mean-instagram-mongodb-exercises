# MongoDB - Aula 02 - Exercício
autor: Carlan Calazans

## Crie uma database chamada be-mean-pokemons

```
$ mongo
MongoDB shell version: 3.0.7
connecting to: test
Mongo-Hacker 0.0.8
bemeaninstagram(mongod-3.0.7) test> use be-mean-pokemons
switched to db be-mean-pokemons
bemeaninstagram(mongod-3.0.7) be-mean-pokemons>
```

## Liste quais databases você possui nesse servidor

```
bemeaninstagram(mongod-3.0.7) be-mean-pokemons> show dbs
be-mean → 0.078GB
local   → 0.078GB
```

## Liste quais coleções você possui nessa database

```
bemeaninstagram(mongod-3.0.7) be-mean-pokemons> show collections
bemeaninstagram(mongod-3.0.7) be-mean-pokemons>
```

## Insira pelo menos 5 pokemons A SUA ESCOLHA utilizando o mesmo padrão de campos utilizado: name, description, attack, defense, height

```
bemeaninstagram(mongod-3.0.7) be-mean-pokemons> var pokemons = [
   {
     "name": "Pikachu",
     "description": "Rato elétrico bem fofinho",
     "type": "eletric",
     "attack": 55,
     "height": 0.4,
     "defense": 34
   },
   {
     "name": "Bulbassauro",
     "description": "Chicote de trepadeira",
     "type": "grama",
     "attack": 49,
     "height": 0.4,
     "defense": 45
   },
   {
     "name": "Charmander",
     "description": "Esse é o co chupando manga de fofinho",
     "type": "fogo",
     "attack": 52,
     "height": 0.6,
     "defense": 14
   },
   {
     "name": "Squirtle",
     "description": "Ejeta água que passarinho no bebe",
     "type": "água",
     "attack": 48,
     "height": 0.5,
     "defense": 67
   },
   {
     "name": "Caterpie",
     "description": "Larva lutadora",
     "type": "inseto",
     "attack": 30,
     "height": 0.3,
     "defense": 35,
     "defense": 22
   }
]
bemeaninstagram(mongod-3.0.7) be-mean-pokemons> db.pokemons.insert(pokemons)
Inserted 1 record(s) in 451ms
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
bemeaninstagram(mongod-3.0.7) be-mean-pokemons> db.pokemons.find().count()
5
```

## Liste os pokemons existentes na sua coleção

```
bemeaninstagram(mongod-3.0.7) be-mean-pokemons> db.pokemons.find()
{
  "_id": ObjectId("564b8a7e89cbf7e2a621e509"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "height": 0.4,
  "defense": 34
}
{
  "_id": ObjectId("564b8a7e89cbf7e2a621e50a"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "defense": 45
}
{
  "_id": ObjectId("564b8a7e89cbf7e2a621e50b"),
  "name": "Charmander",
  "description": "Esse é o co chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "defense": 14
}
{
  "_id": ObjectId("564b8a7e89cbf7e2a621e50c"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho no bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "defense": 67
}
{
  "_id": ObjectId("564b8a7e89cbf7e2a621e50d"),
  "name": "Caterpie",
  "description": "Larva lutadora",
  "type": "inseto",
  "attack": 30,
  "height": 0.3,
  "defense": 22
}
Fetched 5 record(s) in 12ms
```

## Busque `o pokemon a sua escolha pelo nome` e armazene-o em uma variável chamada `poke`

```
bemeaninstagram(mongod-3.0.7) be-mean-pokemons> var poke = db.pokemons.findOne({name: 'Pikachu'})
```

## Modifique sua `description` e salve-o

```
bemeaninstagram(mongod-3.0.7) be-mean-pokemons> poke.description = 'Descricao modificada'
Descricao modificada
bemeaninstagram(mongod-3.0.7) be-mean-pokemons> db.pokemons.save(poke)
Updated 1 existing record(s) in 3ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})
bemeaninstagram(mongod-3.0.7) be-mean-pokemons> db.pokemons.find({name: 'Pikachu'})
{
  "_id": ObjectId("564b8a7e89cbf7e2a621e509"),
  "name": "Pikachu",
  "description": "Descricao modificada",
  "type": "eletric",
  "attack": 55,
  "height": 0.4,
  "defense": 34
}
Fetched 1 record(s) in 0ms
```