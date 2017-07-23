# MongoDB - Aula 03 - Exercício
autor: Rony Souza

## Liste todos Pokemons com a altura menor que 0.5; (passo 1)
```
 > mongo be-mean-pokemons
 > var query = {height: {$lt:0.5}}
 > db.pokemons.find(query)
 > 
 {
  "_id": ObjectId("5650de483a708d4d1c44e60f"),
  "name": "Weedle",
  "description": "Minhoca arregaça cú",
  "type": "bug",
  "attack": 30,
  "defense": 10,
  "height": 0.3
}
{
  "_id": ObjectId("5650f7fc3d5c08c087e86f0f"),
  "name": "Weedle",
  "description": "Minhoca louca",
  "type": "bug",
  "attack": 30,
  "defense": 10,
  "height": 0.3
}
{
  "_id": ObjectId("5651b993ee01bb113f2be176"),
  "name": "Weedle",
  "description": "Minhoca louca",
  "type": "bug",
  "attack": 30,
  "defense": 10,
  "height": 0.3
}

```

## Liste todos Pokemons com a altura maior ou igual que 0.5; (passo 2)

```
db.pokemons.find(query)
{
  "_id": ObjectId("5650de483a708d4d1c44e611"),
  "name": "Rapidash",
  "description": "Ta pegando fogo bixo!",
  "type": "fire",
  "attack": 80,
  "defense": 30,
  "height": 1.7
}
{
  "_id": ObjectId("5650f7fc3d5c08c087e86f11"),
  "name": "Rapidash",
  "description": "On fire!",
  "type": "fire",
  "attack": 80,
  "defense": 30,
  "height": 1.7
}
{
  "_id": ObjectId("5651b993ee01bb113f2be178"),
  "name": "Rapidash",
  "description": "On fire!",
  "type": "fire",
  "attack": 80,
  "defense": 30,
  "height": 1.7
}
{
  "_id": ObjectId("5651e832460fd1a91b124345"),
  "name": "Rapidash",
  "description": "On fire!",
  "type": "fire",
  "attack": 80,
  "defense": 30,
  "height": 1.7
}
{
  "_id": ObjectId("5651e87f460fd1a91b12434a"),
  "name": "Rapidash",
  "description": "On fire!",
  "type": "fire",
  "attack": 80,
  "defense": 30,
  "height": 1.7
}
Fetched 5 record(s) in 3ms

```
## Liste todos Pokemons com a altura menor ou igual que 0.5 E do tipo grama; (passo 3)

```
butu-desktop(mongod-2.4.14) be-mean-pokemons> var query = {$and: [{height: {$lte: 0.5}}, {type: /grama/}]}
butu-desktop(mongod-2.4.14) be-mean-pokemons> query
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

 
```

## Liste todos Pokemons com name 'Pikachu' OU com attack menor ou igual que 0.5 (passo 4)

```
var query = {$or: [{attack: {$lte: 0.5}}, {name: /pikachu/i}]}
query
{
  "$or": [
    {
      "attack": {
        "$lte": 0.5
      }
    },
    {
      "name": /pikachu/i
    }
  ]
}

```
var query = {$e: [{attack: {$gte: 48}}, {height: 0.5}]}
query
{
  "$e": [
    {
      "attack": {
        "$gte": 48
      }
    },
    {
      "height": 0.5
    }
  ]


```

```



