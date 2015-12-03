# MongoDB - Aula 02 - Exercício
Autor: Fabio Gouw

## Criar database (passo 1)
```
Vanaheim(C:\Program Files\MongoDB\Server\3.0\bin\mongod.exe-3.0.6) be-mean> use be-mean-pokemons
switched to db be-mean-pokemons
```

## Listar databases (passo 2)
```
Vanaheim(C:\Program Files\MongoDB\Server\3.0\bin\mongod.exe-3.0.6) be-mean-pokemons> show dbs
be-mean-instagram → 0.078GB
be-mean           → 0.078GB
local             → 0.078GB
test              → 0.078GB
```

## Listar coleções (passo 3)
```
Vanaheim(C:\Program Files\MongoDB\Server\3.0\bin\mongod.exe-3.0.6) be-mean-pokemons> show collections
```

## Cadastrar pokémons (passo 4)
```
Vanaheim(C:\Program Files\MongoDB\Server\3.0\bin\mongod.exe-3.0.6) be-mean-pokemons> var pokemons = [ {name:"Gastly", description: "Fastasma fraquinho", type:"ghost", attack:35, defense:30, height:1.3}, {name:"Haunter", description: "Fantasma mais nervoso", type:"ghost", attack: 50, defense:45, height:1.6}, {name:"Gengar", description:"Fantasma bruto", type:"ghost", attack:65, defense:60, height:1.5}, {name: "Onix", description:"Quase comprei esse carro", type:"rock", attack: 45, defense:160, height:8.79}, {name:"Drowzee", description:"Elefante amarelo feioso", type:"psychic", attack: 48, defense: 45, height:0.99} ]
Vanaheim(C:\Program Files\MongoDB\Server\3.0\bin\mongod.exe-3.0.6) be-mean-pokemons> pokemons
[
  {
    "name": "Gastly",
    "description": "Fastasma fraquinho",
    "type": "ghost",
    "attack": 35,
    "defense": 30,
    "height": 1.3
  },
  {
    "name": "Haunter",
    "description": "Fantasma mais nervoso",
    "type": "ghost",
    "attack": 50,
    "defense": 45,
    "height": 1.6
  },
  {
    "name": "Gengar",
    "description": "Fantasma bruto",
    "type": "ghost",
    "attack": 65,
    "defense": 60,
    "height": 1.5
  },
  {
    "name": "Onix",
    "description": "Quase comprei esse carro",
    "type": "rock",
    "attack": 45,
    "defense": 160,
    "height": 8.79
  },
  {
    "name": "Drowzee",
    "description": "Elefante amarelo feioso",
    "type": "psychic",
    "attack": 48,
    "defense": 45,
    "height": 0.99
  }
]
Vanaheim(C:\Program Files\MongoDB\Server\3.0\bin\mongod.exe-3.0.6) be-mean-pokemons> db.pokemons.insert(pokemons)
Inserted 1 record(s) in 398ms
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

## Listar pokémons (passo 5)
```
Vanaheim(C:\Program Files\MongoDB\Server\3.0\bin\mongod.exe-3.0.6) be-mean-pokemons> db.pokemons.find({})
{
  "_id": ObjectId("565f99d731ad5ca12bfd63fe"),
  "name": "Gastly",
  "description": "Fastasma fraquinho",
  "type": "ghost",
  "attack": 35,
  "defense": 30,
  "height": 1.3
}
{
  "_id": ObjectId("565f99d731ad5ca12bfd63ff"),
  "name": "Haunter",
  "description": "Fantasma mais nervoso",
  "type": "ghost",
  "attack": 50,
  "defense": 45,
  "height": 1.6
}
{
  "_id": ObjectId("565f99d731ad5ca12bfd6400"),
  "name": "Gengar",
  "description": "Fantasma bruto",
  "type": "ghost",
  "attack": 65,
  "defense": 60,
  "height": 1.5
}
{
  "_id": ObjectId("565f99d731ad5ca12bfd6401"),
  "name": "Onix",
  "description": "Quase comprei esse carro",
  "type": "rock",
  "attack": 45,
  "defense": 160,
  "height": 8.79
}
{
  "_id": ObjectId("565f99d731ad5ca12bfd6402"),
  "name": "Drowzee",
  "description": "Elefante amarelo feioso",
  "type": "psychic",
  "attack": 48,
  "defense": 45,
  "height": 0.99
}
Fetched 5 record(s) in 44ms
```

## Encontrar pokemon (passo 6)
```
Vanaheim(C:\Program Files\MongoDB\Server\3.0\bin\mongod.exe-3.0.6) be-mean-pokemons> var query = {name:"Haunter"}
Vanaheim(C:\Program Files\MongoDB\Server\3.0\bin\mongod.exe-3.0.6) be-mean-pokemons> var poke = db.pokemons.findOne(query)
Vanaheim(C:\Program Files\MongoDB\Server\3.0\bin\mongod.exe-3.0.6) be-mean-pokemons> poke
{
  "_id": ObjectId("565f99d731ad5ca12bfd63ff"),
  "name": "Haunter",
  "description": "Fantasma mais nervoso",
  "type": "ghost",
  "attack": 50,
  "defense": 45,
  "height": 1.6
}
```

## Atualização do Pokemon (passo 6)
```
Vanaheim(C:\Program Files\MongoDB\Server\3.0\bin\mongod.exe-3.0.6) be-mean-pokemons> poke.description = "Fantasma assustador #sqn"
Fantasma assustador #sqn
Vanaheim(C:\Program Files\MongoDB\Server\3.0\bin\mongod.exe-3.0.6) be-mean-pokemons> db.pokemons.save(poke)
Updated 1 existing record(s) in 6ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})
Vanaheim(C:\Program Files\MongoDB\Server\3.0\bin\mongod.exe-3.0.6) be-mean-pokemons> poke
{
  "_id": ObjectId("565f99d731ad5ca12bfd63ff"),
  "name": "Haunter",
  "description": "Fantasma assustador #sqn",
  "type": "ghost",
  "attack": 50,
  "defense": 45,
  "height": 1.6
}
```