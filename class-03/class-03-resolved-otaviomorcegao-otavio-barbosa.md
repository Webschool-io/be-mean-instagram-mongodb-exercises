# MongoDB - Aula 03 - Exercício
autor: Otavio Barbosa

## 1 - Liste todos Pokemons com a altura **menor que** 0.5;
```
var query = {height: {$lt: 0.5}}

query
{
  "height": {
    "$lt": 0.5
  }
}

db.pokemons.find(query)
{
  "_id": ObjectId("5642a7833513d84f0c6469de"),
  "name": "Pikachu",
  "description": "Rato eletrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "height": 0.4
}
{
  "_id": ObjectId("5642a88a3513d84f0c6469df"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
{
  "_id": ObjectId("5642ab26b05159d52e714165"),
  "name": "Caterpie",
  "description": "Larva lutadora",
  "type": "inseto",
  "attack": 30,
  "height": 0.3,
  "defense": 35
}
Fetched 3 record(s) in 12ms

```

## 2 - Liste todos Pokemons com a altura **maior ou igual que** 0.5
```
var query = {height: {$gte: 0.5}}

query
{
  "height": {
    "$gte": 0.5
  }
}

db.pokemons.find(query)
{
  "_id": ObjectId("5642a8c93513d84f0c6469e0"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6
}
{
  "_id": ObjectId("5642a9073513d84f0c6469e1"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5
}
{
  "_id": ObjectId("56441607dd2474f79af14ae4"),
  "name": "Didimon",
  "description": "Pokemon do Ceará",
  "type": "cabeçudo",
  "attack": 45,
  "defense": 30,
  "height": 1.6
}
{
  "_id": ObjectId("56441607dd2474f79af14ae5"),
  "name": "Dedemon",
  "description": "Melhor amigo do cearense, será?",
  "type": "lesado",
  "attack": 41,
  "defense": 32,
  "height": 1.7
}
{
  "_id": ObjectId("56441607dd2474f79af14ae6"),
  "name": "Mussumon",
  "description": "Movido a mé!",
  "type": "pinguço",
  "attack": 48,
  "defense": 25,
  "height": 1.8
}
{
  "_id": ObjectId("56441607dd2474f79af14ae7"),
  "name": "Zacamon",
  "description": "O pokemon de peruca",
  "type": "menino",
  "attack": 39,
  "defense": 39,
  "height": 1.5
}
Fetched 6 record(s) in 8ms

```

## 3 - Liste todos Pokemons com a altura **menor ou igual que** 0.5 **E** do tipo grama
```
var query = {$and: [{height: {$lte: 0.5}}, {type: /grama/}]}

query
{
  "$and": [
    {
      "height": {
        "$lte": 0.5
      }
    },
    {
      "type": /grama/
    }
  ]
}

db.pokemons.find(query)
{
  "_id": ObjectId("5642a88a3513d84f0c6469df"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
Fetched 1 record(s) in 9ms

```

## 4 - Liste todos Pokemons com o name `Pikachu` **OU** com attack **menor ou igual que** 0.5
```
var query = {$or: [{attack: {$lte: 0.5}}, {name: /Pikachu/i}]}

query
{
  "$or": [
    {
      "attack": {
        "$lte": 0.5
      }
    },
    {
      "name": /Pikachu/i
    }
  ]
}

db.pokemons.find(query)
{
  "_id": ObjectId("5642a7833513d84f0c6469de"),
  "name": "Pikachu",
  "description": "Rato eletrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "height": 0.4
}
Fetched 1 record(s) in 10ms
```

## 5 - Liste todos Pokemons com o attack **MAIOR OU IGUAL QUE** 48 **E** com  height **menor ou igual que** 0.5
```
var query = {$and: [{attack: {$gte: 48}}, {height: {$lte: 0.5}}]}

query
{
  "$and": [
    {
      "attack": {
        "$gte": 48
      }
    },
    {
      "height": {
        "$lte": 0.5
      }
    }
  ]
}

db.pokemons.find(query)
{
  "_id": ObjectId("5642a7833513d84f0c6469de"),
  "name": "Pikachu",
  "description": "Rato eletrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "height": 0.4
}
{
  "_id": ObjectId("5642a88a3513d84f0c6469df"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
{
  "_id": ObjectId("5642a9073513d84f0c6469e1"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5
}
Fetched 3 record(s) in 5ms

```


