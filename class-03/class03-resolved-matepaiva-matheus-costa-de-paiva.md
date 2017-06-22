# MongoDB - Aula 03 - Exercício
autor: Matheus Costa de Paiva

## Liste todos Pokemons com a altura **menor que** 0.5;
```
  levelho(mongod-3.0.7) be-mean-pokemons> var query = {height: {$lt:0.5}}
  levelho(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
  Fetched 0 record(s) in 0ms
  levelho(mongod-3.0.7) be-mean-pokemons> 
```

## Liste todos Pokemons com a altura **maior ou igual que** 0.5
```
  levelho(mongod-3.0.7) be-mean-pokemons> var query = {height: {$gte:0.5}}
  levelho(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
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
    "description": "Um pokemon que passarinho não bebe",
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
  Fetched 5 record(s) in 3ms
```

## Liste todos Pokemons com a altura **menor ou igual que** 0.5 **E** do tipo grama
```
  levelho(mongod-3.0.7) be-mean-pokemons> var query = {$and:[{height: {$lte:0.5}},{type:"grama"}]}
  levelho(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
  Fetched 0 record(s) in 0ms
```

## Liste todos Pokemons com o name `Pikachu` **OU** com attack **menor ou igual que** 0.5
```
  levelho(mongod-3.0.7) be-mean-pokemons> var query = {$or:[{name: "Pikachu"},{attack:{$lte:0.5}}]}
  levelho(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
  Fetched 0 record(s) in 1ms

```

## Liste todos Pokemons com o attack **MAIOR OU IGUAL QUE** 48 **E** com  height **menor ou igual que**  0.5
```
  levelho(mongod-3.0.7) be-mean-pokemons> var query = {$and:[{height: {$lte:0.5}},{attack:{$gte:48}}]}
  levelho(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
  Fetched 0 record(s) in 1ms
```