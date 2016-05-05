# MongoDB - Aula 02 - Exercício
Autor: Simone Amorim

## Criação da database be-mean-pokemons(passo 1)
 
```
C:\Users\simone>mongo
MongoDB shell version: 3.0.7
connecting to: test
use be-mean-pokemons
switched to db be-mean-pokemons
```

## Listagem das databases (passo 2)

```
show dbs
be-mean            0.078GB
be-mean-instagram  0.078GB
be-mean-pokemons   0.078GB
local              0.078GB
```

## Listagem das coleções (passo 3)

```
show collections
pokemons
system.indexes
```

## Cadastro dos pokemons (passo 4)

```
var pokemon = 
[
	{
	  "name": "Mew",
	  "description": "Criador de todos os pokemons",
	  "type": "psíquico",
	  "attack": 100,
	  "height": 0.41
	},

	{
      "name": "Raikou",
      "description": "A fera lendária do raio",
      "type": "elétrico",
      "attack": 85,
      "height": 1.91
    },

	{
      "name": "Entei",
      "description": "Veloz pokemon do fogo",
      "type": "fogo",
      "attack": 115,
      "height": 2.11
    },

	{
      "name": "Suicine",
      "description": "Cão lendário que controla as águas",
      "type": "água",
      "attack": 75,
      "height": 2.01
    },

	{
      "name": "Charizard",
      "description": "Conhecido como dragão inimigo de são jorge",
      "type": "fogo",
      "attack": 84,
      "height": 1.70
    }
 ]

db.pokemons.insert(pokemon)
BulkWriteResult({
        "writeErrors" : [ ],
        "writeConcernErrors" : [ ],
        "nInserted" : 5,
        "nUpserted" : 0,
        "nMatched" : 0,
        "nModified" : 0,
        "nRemoved" : 0,
        "upserted" : [ ]
})
```

## Lista dos pokemons (passo 5)

```
db.pokemons.find()
{ "_id" : ObjectId("56b0dbb8d50150923e9d15af"), "name" : "Mew", "description" : "Criador de todos os pokemons", "type" : "psíquico", "attack" : 100, "height" : 0.41 }
{ "_id" : ObjectId("56b0dbb8d50150923e9d15b0"), "name" : "Raikou", "description" : "A fera lendária do raio", "type" : "elétrico", "attack" : 85, "height" : 1.91 }
{ "_id" : ObjectId("56b0dbb8d50150923e9d15b1"), "name" : "Entei", "description" : "Veloz pokemon do fogo", "type" : "fogo", "attack" : 115, "height" : 2.11 }
{ "_id" : ObjectId("56b0dbb8d50150923e9d15b2"), "name" : "Suicine", "description" : "Cão lendário que controla as águas", "type" : "água", "attack" : 75, "height" : 2.01 }
{ "_id" : ObjectId("56b0dbb8d50150923e9d15b3"), "name" : "Charizard", "description" : "Conhecido como dragão inimigo de são jorge", "type" : "fogo", "attack" : 84, "height" : 1.7 }
```

## Buscando um pokemon aleatório e armazenando na variável poke (passo 6)

```
var query = {name: 'Mew'}
var poke = db.pokemons.findOne(query)
poke
{
        "_id" : ObjectId("56b0dbb8d50150923e9d15af"),
        "name" : "Mew",
        "description" : "Criador de todos os pokemons",
        "type" : "psíquico",
        "attack" : 100,
        "height" : 0.41
}
```

## Atualização do pokemon localiado no passo 6 (passo 7)

```
poke.description = 'Gatinho mais fofinho que já vi!'
Gatinho mais fofinho que já vi!
poke
{
        "_id" : ObjectId("56b0dbb8d50150923e9d15af"),
        "name" : "Mew",
        "description" : "Gatinho mais fofinho que já vi!",
        "type" : "psíquico",
        "attack" : 100,
        "height" : 0.41
}

db.pokemons.save(poke)
WriteResult({ "nMatched" : 1, "nUpserted" : 0, "nModified" : 1 })
db.pokemons.find()
{ "_id" : ObjectId("56b0dbb8d50150923e9d15af"), "name" : "Mew", "description" : "Gatinho mais fofinho que já vi!", "type" : "psíquico", "attack" : 100, "height" : 0.41 }
{ "_id" : ObjectId("56b0dbb8d50150923e9d15b0"), "name" : "Raikou", "description" : "A fera lendária do raio", "type" : "elétrico", "attack" : 85, "height" : 1.91 }
{ "_id" : ObjectId("56b0dbb8d50150923e9d15b1"), "name" : "Entei", "description" : "Veloz pokemon do fogo", "type" : "fogo", "attack" : 115, "height" : 2.11 }
{ "_id" : ObjectId("56b0dbb8d50150923e9d15b2"), "name" : "Suicine", "description" : "Cão lendário que controla as águas", "type" : "água", "attack" : 75, "height" : 2.01 }
{ "_id" : ObjectId("56b0dbb8d50150923e9d15b3"), "name" : "Charizard", "description" : "Conhecido como dragão inimigo de são jorge", "type" : "fogo", "attack"
```
