# MongoDB - Aula 03 - Exercício
autor: Franklin Dias


## Liste todos Pokemons com a altura **menor que** 0.5;

```
localhost(mongod-2.6.11) pokemons> var query = {"height": {$lt:0.5}}
localhost(mongod-2.6.11) pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("564352978b7f0c7f55da6511"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 55,
  "height": 0.4
}
{
  "_id": ObjectId("564352e58b7f0c7f55da6512"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
{
  "_id": ObjectId("56435452a887a8736a8f27d6"),
  "name": "Caterpie",
  "description": "Larva lutadora",
  "type": "inseto",
  "attack": 30,
  "height": 0.3,
  "defense": 35
}
Fetched 3 record(s) in 3ms


```

## Liste todos Pokemons com a altura **maior ou igual que** 0.5

```
localhost(mongod-2.6.11) pokemons> var query = {"height": {$gte:0.5}}
localhost(mongod-2.6.11) pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("564352f48b7f0c7f55da6513"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6
}
{
  "_id": ObjectId("56435395a887a8736a8f27d5"),
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
var query = {$and: [{"height":{$lte: 0.5} }, {"type": "Grama"} ]}
localhost(mongod-2.6.11) pokemons> db.pokemons.find(query)
Fetched 0 record(s) in 0ms

```

## Liste todos Pokemons com o name `Pikachu` **OU** com attack **menor ou igual que** 0.5

```
localhost(mongod-2.6.11) pokemons> var query = {$or: [{"name": "Pikachu"}, {"attack": {$lte:0.5} }]}
localhost(mongod-2.6.11) pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("564352978b7f0c7f55da6511"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 55,
  "height": 0.4
}
Fetched 1 record(s) in 2ms


```

## Liste todos Pokemons com o attack **MAIOR OU IGUAL QUE** 48 **E** com  height **menor ou igual que** 0.5

```
localhost(mongod-2.6.11) pokemons> var query = {$and: [{"attack":{$gte: 48} },{"height": {$lte: 0.5} } ]}
localhost(mongod-2.6.11) pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("564352978b7f0c7f55da6511"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 55,
  "height": 0.4
}
{
  "_id": ObjectId("564352e58b7f0c7f55da6512"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
{
  "_id": ObjectId("56435395a887a8736a8f27d5"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5
}
Fetched 3 record(s) in 1ms

```