# MongoDb - Aula 03 - Exercício

autor: **Bruno Rodrigues**

## Liste todos Pokemons com a altura **menor que** 0.5

```
bruno-dev(mongod-3.0.7) be-mean-instagram> var query = {height: {$lt:0.5}}
bruno-dev(mongod-3.0.7) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("565a2169b2243c98db16f00a"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 55,
  "height": 0.4
}
{
  "_id": ObjectId("565a21f8b2243c98db16f00b"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
Fetched 2 record(s) in 1ms

```

## Liste todos Pokemons com a altura **maior ou igual que** 0.5

```
bruno-dev(mongod-3.0.7) be-mean-instagram> var query = {height: {$gte:0.5}}
bruno-dev(mongod-3.0.7) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("565a221bb2243c98db16f00c"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6
}
{
  "_id": ObjectId("565a2260b2243c98db16f00d"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5
}
Fetched 2 record(s) in 1ms

```

## Liste todos Pokemons com a altura **menor ou igual que** 0.5 **E** do tipo grama

```

bruno-dev(mongod-3.0.7) be-mean-instagram> var query1 = {height: {$lte:0.5}}
bruno-dev(mongod-3.0.7) be-mean-instagram> var query2 = {type: 'grama'}
bruno-dev(mongod-3.0.7) be-mean-instagram> db.pokemons.find({$and: [query1, query2]})
{
  "_id": ObjectId("565a21f8b2243c98db16f00b"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
Fetched 1 record(s) in 0ms


```

## Liste todos Pokemons com o name `Pikachu` **OU** com attack **menor ou igual que** 0.5

```
bruno-dev(mongod-3.0.7) be-mean-instagram> var query = {$or: [{name: 'Pikachu'},{attack:{$lte: 0.5}}]}
bruno-dev(mongod-3.0.7) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("565a2169b2243c98db16f00a"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 55,
  "height": 0.4
}
Fetched 1 record(s) in 1ms


```

## Liste todos Pokemons com o attack **MAIOR OU IGUAL QUE** 48 **E** com  height **menor ou igual que** 0.5

```

bruno-dev(mongod-3.0.7) be-mean-instagram> var query = {$and: [{height: {$lte: 0.5}},{attack:{$gte: 48}}]}
bruno-dev(mongod-3.0.7) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("565a2169b2243c98db16f00a"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 55,
  "height": 0.4
}
{
  "_id": ObjectId("565a21f8b2243c98db16f00b"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
{
  "_id": ObjectId("565a2260b2243c98db16f00d"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5
}
Fetched 3 record(s) in 2ms


```


## Envio

```
                                \o/
```
