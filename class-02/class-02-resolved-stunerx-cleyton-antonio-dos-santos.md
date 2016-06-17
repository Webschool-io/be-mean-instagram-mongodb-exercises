###MongoDB - Aula 02 - Exercício
Autor: Cleyton Antonio dos Santos

##Criando database
```
stunerx(mongod-2.6.10) be-mean-teste> use be-mean-pokemons
switched to db be-mean-pokemons

```

##Listando databases
```
donato-dell(mongod-3.2.4) be-mean-pokemons> show dbs
stunerx(mongod-2.6.10) be-mean-pokemons> show dbs
admin             → (empty)
be-mean           → 0.078GB
be-mean-instagram → 0.078GB
be-mean-teste     → 0.078GB
local             → 0.078GB
```

##Listando collections
```
stunerx(mongod-2.6.10) be-mean-pokemons> show collections
stunerx(mongod-2.6.10) be-mean-pokemons>  
```

##Cadastro de pokemons
```


var pokemons = [
{"name":"Metapod","description":"The shell covering this Pokémon's body is as hard as an iron slab","type":"inseto", "attack":1, "height": 0.7},
{"name":"Pidgey","description":"Pidgey tem um extremo senso de direção","type":"voador", "attack":2, "height": 0.3},
{"name":"Jigglypuff","description":"Esse pokemon pode cantar","type":"fada","attack":2, "height": 0.5},
{"name":"Growlithe","description":"Growlithe tem um super faro","type":"fogo","attack":4, "height": 0.7},
{"name":"Psyduck","description":"Psyduck tem um poder misterioso","type":"agua", "attack":3, "height": 0.8}
]


stunerx(mongod-2.6.10) be-mean-pokemons> pokemons
[
  {
    "name": "Metapod",
    "description": "The shell covering this Pokémon's body is as hard as an iron slab",
    "type": "inseto",
    "attack": 1,
    "height": 0.7
  },
  {
    "name": "Pidgey",
    "description": "Pidgey tem um extremo senso de direção",
    "type": "voador",
    "attack": 2,
    "height": 0.3
  },
  {
    "name": "Jigglypuff",
    "description": "Esse pokemon pode cantar",
    "type": "fada",
    "attack": 2,
    "height": 0.5
  },
  {
    "name": "Growlithe",
    "description": "Growlithe tem um super faro",
    "type": "fogo",
    "attack": 4,
    "height": 0.7
  },
  {
    "name": "Psyduck",
    "description": "Psyduck tem um poder misterioso",
    "type": "agua",
    "attack": 3,
    "height": 0.8
  }
]


stunerx(mongod-2.6.10) be-mean-pokemons> db.pokemons.insert(pokemons)
][Inserted 1 record(s) in 250ms
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

##Lista dos pokemons
```
stunerx(mongod-2.6.10) be-mean-pokemons> db.pokemons.find()
{
  "_id": ObjectId("57643a3ad7ba6d657212bc44"),
  "name": "Metapod",
  "description": "The shell covering this Pokémon's body is as hard as an iron slab",
  "type": "inseto",
  "attack": 1,
  "height": 0.7
}
{
  "_id": ObjectId("57643a3ad7ba6d657212bc45"),
  "name": "Pidgey",
  "description": "Pidgey tem um extremo senso de direção",
  "type": "voador",
  "attack": 2,
  "height": 0.3
}
{
  "_id": ObjectId("57643a3ad7ba6d657212bc46"),
  "name": "Jigglypuff",
  "description": "Esse pokemon pode cantar",
  "type": "fada",
  "attack": 2,
  "height": 0.5
}
{
  "_id": ObjectId("57643a3ad7ba6d657212bc47"),
  "name": "Growlithe",
  "description": "Growlithe tem um super faro",
  "type": "fogo",
  "attack": 4,
  "height": 0.7
}
{
  "_id": ObjectId("57643a3ad7ba6d657212bc48"),
  "name": "Psyduck",
  "description": "Psyduck tem um poder misterioso",
  "type": "agua",
  "attack": 3,
  "height": 0.8
}

Fetched 5 record(s) in 6ms


```

##Pokemon
```
stunerx(mongod-2.6.10) be-mean-pokemons> var query = {"name": "Growlithe"}
stunerx(mongod-2.6.10) be-mean-pokemons> var poke = db.pokemons.findOne(query)
stunerx(mongod-2.6.10) be-mean-pokemons> poke
{
  "_id": ObjectId("57643a3ad7ba6d657212bc47"),
  "name": "Growlithe",
  "description": "Growlithe tem um super faro",
  "type": "fogo",
  "attack": 4,
  "height": 0.7
}

stunerx(mongod-2.6.10) be-mean-pokemons> poke.name
Growlithe



```

##Atualização do Pokemon
```
stunerx(mongod-2.6.10) be-mean-pokemons> poke.description
Growlithe tem um super faro
stunerx(mongod-2.6.10) be-mean-pokemons> poke.description = "Cachorro louco monstrão"
Cachorro louco monstrão
stunerx(mongod-2.6.10) be-mean-pokemons> db.pokemons.save(poke)
Updated 1 existing record(s) in 14ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})
stunerx(mongod-2.6.10) be-mean-pokemons> var pokeAtualizado = db.pokemons.find(query)
stunerx(mongod-2.6.10) be-mean-pokemons> pokeAtualizado
{
  "_id": ObjectId("57643a3ad7ba6d657212bc47"),
  "name": "Growlithe",
  "description": "Cachorro louco monstrão",
  "type": "fogo",
  "attack": 4,
  "height": 0.7
}
Fetched 1 record(s) in 1ms


```