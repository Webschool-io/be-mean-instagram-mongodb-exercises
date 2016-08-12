# MongoDB - Aula 03 - Exercício
autor: Francisco Daniel Costa

## 1. Liste todos Pokemons com a altura menor que 0.5

```
insta-mongodb(mongod-3.2.8) mean-pokemon> var query = {'height': {$lt: 0.5}}
insta-mongodb(mongod-3.2.8) mean-pokemon> query
{
  "height": {
    "$lt": 0.5
  }
}
insta-mongodb(mongod-3.2.8) mean-pokemon> db.pokemons.find(query)
{
  "_id": ObjectId("5798c7498fb9d00c3188d3ab"),
  "name": "Xikó",
  "description": "Grão de bico violento",
  "defense": 1,
  "attack": 90,
  "height": 0.4
}
{
  "_id": ObjectId("5798c7498fb9d00c3188d3ac"),
  "name": "Borrão",
  "description": "Jungle Lui",
  "defense": 5,
  "attack": 90,
  "height": 0.2
}
Fetched 2 record(s) in 1ms
```

## 2. Liste todos Pokemons com a altura maior ou igual que 0.5

```
insta-mongodb(mongod-3.2.8) mean-pokemon> var query = {'height': {$gte: 0.5}}
insta-mongodb(mongod-3.2.8) mean-pokemon> db.pokemons.find(query)
{
  "_id": ObjectId("5798c7498fb9d00c3188d3aa"),
  "name": "Roska",
  "description": "Quebra e depois conserta",
  "defense": 10,
  "attack": 55,
  "height": 0.5
}
{
  "_id": ObjectId("5798c7498fb9d00c3188d3ad"),
  "name": "Ameba",
  "description": "Nossa, cara",
  "defense": 40,
  "attack": 60,
  "height": 0.6
}
{
  "_id": ObjectId("5798c7498fb9d00c3188d3ae"),
  "name": "Bruxa",
  "description": "Põe a 5",
  "defense": 50,
  "attack": 10,
  "height": 0.7
}
{
  "_id": ObjectId("5798c7498fb9d00c3188d3af"),
  "name": "Moncherry",
  "description": "O macho nunca afina",
  "defense": 70,
  "attack": 5,
  "height": 0.8
}
Fetched 4 record(s) in 3ms	 
```

## 3. Liste todos Pokemons com a altura menor ou igual que 0.5 E do tipo grama

```
insta-mongodb(mongod-3.2.8) mean-pokemon> var query = { $and : [ { 'height': {$lte: 0.5} } , { 'type' : 'grama' } ] } 
insta-mongodb(mongod-3.2.8) mean-pokemon> query
{
  "$and": [
    {
      "height": {
        "$lte": 0.5
      }
    },
    {
      "type": "grama"
    }
  ]
}
insta-mongodb(mongod-3.2.8) mean-pokemon> db.pokemons.find(query)
Fetched 0 record(s) in 1ms
```

## 4. Liste todos Pokemons com o name `Pikachu` OU com attack menor ou igual que 0.5

```
insta-mongodb(mongod-3.2.8) mean-pokemon> var query = { $or : [ {'name': 'Pikachu'},  { 'attack': {$lte: 0.5} }  ] }
insta-mongodb(mongod-3.2.8) mean-pokemon> query
{
  "$or": [
    {
      "name": "Pikachu"
    },
    {
      "attack": {
        "$lte": 0.5
      }
    }
  ]
}
insta-mongodb(mongod-3.2.8) mean-pokemon> db.pokemons.find(query)
Fetched 0 record(s) in 0ms
```

## 5. Liste todos Pokemons com o attack MAIOR OU IGUAL QUE 48 E com  height menor ou igual que 0.5

```
insta-mongodb(mongod-3.2.8) mean-pokemon> var query = { $or : [ {'attack': {$gte: 48}},  { 'height': {$lte: 0.5} } ]}
insta-mongodb(mongod-3.2.8) mean-pokemon> query
{
  "$or": [
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
insta-mongodb(mongod-3.2.8) mean-pokemon> db.pokemons.find(query)
        "$gte": 48
{
  "_id": ObjectId("5798c7498fb9d00c3188d3aa"),
  "name": "Roska",
  "description": "Quebra e depois conserta",
  "defense": 10,
  "attack": 55,
  "height": 0.5
}
{
  "_id": ObjectId("5798c7498fb9d00c3188d3ab"),
  "name": "Xikó",
  "description": "Grão de bico violento",
  "defense": 1,
  "attack": 90,
  "height": 0.4
}
{
  "_id": ObjectId("5798c7498fb9d00c3188d3ac"),
  "name": "Borrão",
  "description": "Jungle Lui",
  "defense": 5,
  "attack": 90,
  "height": 0.2
}
{
  "_id": ObjectId("5798c7498fb9d00c3188d3ad"),
  "name": "Ameba",
  "description": "Nossa, cara",
  "defense": 40,
  "attack": 60,
  "height": 0.6
}
Fetched 4 record(s) in 3ms
```

