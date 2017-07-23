# MongoDB - Aula 03 - Exercício
autor: Aguinaldo Alves Barbosa silva

## Listagem pokemons height < 0.5

```
MacBook-Pro-de-Aguinaldo(mongod-3.1.9) be-mean-pokemons> var q = {height : { $lt: 0.5} }
MacBook-Pro-de-Aguinaldo(mongod-3.1.9) be-mean-pokemons> db.pokemons.find(q)

{
  "_id": ObjectId("5653a41a8fcd0c51644156e6"),
  "name": "Pikachu",
  "description": "Rato Eletrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "height": 0.4
}
{
  "_id": ObjectId("5653a4688fcd0c51644156e7"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
{
  "_id": ObjectId("5653a50e8fcd0c51644156e9"),
  "name": "Caterpiee",
  "description": "Larva lutadora ",
  "type": "inseto",
  "attack": 30,
  "height": 0.3,
  "defense": 35
}
Fetched 3 record(s) in 10ms

```

## Listagem pokemons height >= 0.5

```
var q = {height : { $gte: 0.5} }
MacBook-Pro-de-Aguinaldo(mongod-3.1.9) be-mean-pokemons> db.pokemons.find(q)

{
  "_id": ObjectId("5653a4b08fcd0c51644156e8"),
  "name": "Chamander",
  "description": "Este é  o cão chupando manda de fofinho ",
  "type": "fogo",
  "attack": 52,
  "height": 0.6
}
{
  "_id": ObjectId("5653a5358fcd0c51644156ea"),
  "name": "Squirtle",
  "description": "Ejata água que passarinho não bebe ",
  "type": "água",
  "attack": 48,
  "height": 0.5
}
Fetched 2 record(s) in 2ms


```

## Listagem pokemons height <= 0.5 e type "grama"

```
MacBook-Pro-de-Aguinaldo(mongod-3.1.9) be-mean-pokemons> var q = {$and: [{height: {$lte: 0.5}},{type: "grama"}]}
MacBook-Pro-de-Aguinaldo(mongod-3.1.9) be-mean-pokemons> db.pokemons.find(q)

{
  "_id": ObjectId("5653a4688fcd0c51644156e7"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
Fetched 1 record(s) in 1ms

```

## Listagem pokemons name "Pikachu" ou attack <= 0.5

```
MacBook-Pro-de-Aguinaldo(mongod-3.1.9) be-mean-pokemons> var q = {$or: [{name: "Pikachu"}, {attack: {$lte: 0.5}}]}
MacBook-Pro-de-Aguinaldo(mongod-3.1.9) be-mean-pokemons> db.pokemons.find(q)
{
  "_id": ObjectId("5653a41a8fcd0c51644156e6"),
  "name": "Pikachu",
  "description": "Rato Eletrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "height": 0.4
}
Fetched 1 record(s) in 1ms

```
## Listagem pokemons attack >= 48 e height <= 0.5
``
MacBook-Pro-de-Aguinaldo(mongod-3.1.9) be-mean-pokemons> var q = {$and: [{attack: {$gte: 48}}, {height: {$lte: 0.5}}]}
MacBook-Pro-de-Aguinaldo(mongod-3.1.9) be-mean-pokemons> db.pokemons.find(q)
{
  "_id": ObjectId("5653a41a8fcd0c51644156e6"),
  "name": "Pikachu",
  "description": "Rato Eletrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "height": 0.4
}
{
  "_id": ObjectId("5653a4688fcd0c51644156e7"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
{
  "_id": ObjectId("5653a5358fcd0c51644156ea"),
  "name": "Squirtle",
  "description": "Ejata água que passarinho não bebe ",
  "type": "água",
  "attack": 48,
  "height": 0.5
}
Fetched 3 record(s) in 2ms

```