# MongoDB - Aula 03 - Exercício
autor: Ademílson F. Tonato

## Liste todos Pokemons com a altura **menor que** 0.5

```
lucasft(mongod-2.6.10) be-mean-pokemons> var query = {height: {$lt: 0.5}}
lucasft(mongod-2.6.10) be-mean-pokemons> db.pokemons.find(query)
Fetched 0 record(s) in 0ms
```

## Liste todos Pokemons com a altura **maior ou igual que** 0.5

```
lucasft(mongod-2.6.10) be-mean-pokemons> var query = {height: {$gte: 0.5}}
lucasft(mongod-2.6.10) be-mean-pokemons> db.pokemons.find(query)
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
  "description": "A descrição foi alterada :)",
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

## Liste todos Pokemons com a altura **menor ou igual que** 0.5 **E** do tipo grama

```
lucasft(mongod-2.6.10) be-mean-pokemons> var query = {$and: [{height: {$lte: 0.5}}, {type: 'grama'}]}
lucasft(mongod-2.6.10) be-mean-pokemons> db.pokemons.find(query)
Fetched 0 record(s) in 1ms
```

## Liste todos Pokemons com o name `Pikachu` **OU** com attack **menor ou igual que** 0.5

```
lucasft(mongod-2.6.10) be-mean-pokemons> var query = {$or: [{attack: {$lte: 0.5}}, {name: 'pikachu'}]}
lucasft(mongod-2.6.10) be-mean-pokemons> query
{
  "$or": [
    {
      "attack": {
        "$lte": 0.5
      }
    },
    {
      "name": "pikachu"
    }
  ]
}
lucasft(mongod-2.6.10) be-mean-pokemons> db.pokemons.find(query)
Fetched 0 record(s) in 0ms
```

## Liste todos Pokemons com o attack **MAIOR OU IGUAL QUE** 48 **E** com  height **menor ou igual que** 0.5

```
lucasft(mongod-2.6.10) be-mean-pokemons> var query = {$and: [{attack: {$gte: 48}}, {height: {$lte: 0.5}}]}
lucasft(mongod-2.6.10) be-mean-pokemons> db.pokemons.find(query)
Fetched 0 record(s) in 1ms
```