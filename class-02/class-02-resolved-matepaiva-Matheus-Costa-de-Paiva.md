###MongoDB - Aula 02 - Exercício
Autor: Matheus Costa de Paiva

##Criando database
```
	MongoDB shell version: 3.0.7
	connecting to: test
	Mongo-Hacker 0.0.9
	levelho(mongod-3.0.7) test> use be-mean-pokemons
	switched to db be-mean-pokemons
	levelho(mongod-3.0.7) be-mean-pokemons> 

```

##Listando databases
```
	levelho(mongod-3.0.7) be-mean-pokemons> show dbs
	local   → 0.078GB
	be-mean → 0.078GB
	test    → 0.078GB
	levelho(mongod-3.0.7) be-mean-pokemons> 
```

##Listando collections
```
	levelho(mongod-3.0.7) be-mean-pokemons> show collections
	levelho(mongod-3.0.7) be-mean-pokemons> 
```

##Cadastro dos pokemons
```
  levelho(mongod-3.0.7) be-mean-pokemons> var pokemons=[
  ...     {
  ...       name: "Mongomon",
  ...       description: "Um pokemon não-relacional",
  ...       type: "bedeomon",
  ...       attack: 42,
  ...       defense: 42,
  ...       height: 42
  ...     },{
  ...       name: "Mateomon",
  ...       description: "Um pokemon que se bebe",
  ...       type: "bebeomon",
  ...       attack: 69,
  ...       defense: 96,
  ...       height: 12
  ...     },{
  ...       name: "Sabedomon",
  ...       description: "Um pokemon que sabe das coisas.",
  ...       type: "cebeomon",
  ...       attack: 55,
  ...       defense: 77,
  ...       height: 66
  ...     },{
  ...       name: "Criativomon",
  ...       description: "Um pokemon que pensa ser publicitário",
  ...       type: "pepeomon",
  ...       attack: 3,
  ...       defense: 1,
  ...       height: 100
  ...     },{
  ...       name: "Facebokomon",
  ...       description: "Um pokemon social",
  ...       type: "redomon",
  ...       attack: 77,
  ...       defense: 33,
  ...       height: 124
  ...     }
  ... ]
  levelho(mongod-3.0.7) be-mean-pokemons> db.pokemons.insert(pokemons)
  Inserted 1 record(s) in 620ms
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
  levelho(mongod-3.0.7) be-mean-pokemons> 
```

##Lista de todos os pokemons
```
  levelho(mongod-3.0.7) be-mean-pokemons> db.pokemons.find()
  {
    "_id": ObjectId("566a1c25f16b47e8550adb43"),
    "name": "Mongomon",
    "description": "Um pokemon não-relacional",
    "type": "bedeomon",
    "attack": 42,
    "defense": 42,
    "height": 42
  }
  {
    "_id": ObjectId("566a1c25f16b47e8550adb44"),
    "name": "Mateomon",
    "description": "Um pokemon que se bebe",
    "type": "bebeomon",
    "attack": 69,
    "defense": 96,
    "height": 12
  }
  {
    "_id": ObjectId("566a1c25f16b47e8550adb45"),
    "name": "Sabedomon",
    "description": "Um pokemon que sabe das coisas.",
    "type": "cebeomon",
    "attack": 55,
    "defense": 77,
    "height": 66
  }
  {
    "_id": ObjectId("566a1c25f16b47e8550adb46"),
    "name": "Criativomon",
    "description": "Um pokemon que pensa ser publicitário",
    "type": "pepeomon",
    "attack": 3,
    "defense": 1,
    "height": 100
  }
  {
    "_id": ObjectId("566a1c25f16b47e8550adb47"),
    "name": "Facebokomon",
    "description": "Um pokemon social",
    "type": "redomon",
    "attack": 77,
    "defense": 33,
    "height": 124
  }
  Fetched 5 record(s) in 35ms
  levelho(mongod-3.0.7) be-mean-pokemons> 
```

##Query para buscar o pokemon
```
  levelho(mongod-3.0.7) be-mean-pokemons> var query = {name: 'Mateomon'}
  levelho(mongod-3.0.7) be-mean-pokemons> var poke = db.pokemons.findOne(query)
  levelho(mongod-3.0.7) be-mean-pokemons> poke
  {
    "_id": ObjectId("566a1c25f16b47e8550adb44"),
    "name": "Mateomon",
    "description": "Um pokemon que se bebe",
    "type": "bebeomon",
    "attack": 69,
    "defense": 96,
    "height": 12
  }
```

##Atualizando a descrição do Pokemon
```
  levelho(mongod-3.0.7) be-mean-pokemons> poke.description = "Um pokemon que passarinho não bebe"
  Um pokemon que passarinho não bebe
  levelho(mongod-3.0.7) be-mean-pokemons> db.pokemons.save(poke)
  Updated 1 existing record(s) in 36ms
  WriteResult({
    "nMatched": 1,
    "nUpserted": 0,
    "nModified": 1
  })
  levelho(mongod-3.0.7) be-mean-pokemons> db.pokemons.findOne(query)
  {
    "_id": ObjectId("566a1c25f16b47e8550adb44"),
    "name": "Mateomon",
    "description": "Um pokemon que passarinho não bebe",
    "type": "bebeomon",
    "attack": 69,
    "defense": 96,
    "height": 12
  }
  levelho(mongod-3.0.7) be-mean-pokemons> 
```
