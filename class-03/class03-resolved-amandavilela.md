# MongoDB - Aula 03 - Exercício
autor: Amanda Vilela

## Listando todos os pokemons com altura menor que 0.5

```
amanda-Inspiron-7520(mongod-2.4.9) be-mean> var query = {height: {$lt:0.5}}
amanda-Inspiron-7520(mongod-2.4.9) be-mean> db.pokemons.find(query)
{
  "_id": ObjectId("5651f21e2b465aac30102fea"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "height": 0.4
}
{
  "_id": ObjectId("5651f3132b465aac30102feb"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
{
  "_id": ObjectId("5651f44e2b465aac30102fef"),
  "name": "Caterpie",
  "description": "Larva lutadora",
  "type": "inseto",
  "attack": 30,
  "height": 0.3,
  "defense": 35
}
Fetched 3 record(s) in 0ms

```

## Listando todos os pokemons com altura maior ou igual que 0.5

```
amanda-Inspiron-7520(mongod-2.4.9) be-mean> var query = {height: {$gte:0.5}}
amanda-Inspiron-7520(mongod-2.4.9) be-mean> db.pokemons.find(query)
{
  "_id": ObjectId("5651f3592b465aac30102fed"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6
}
{
  "_id": ObjectId("5651f3912b465aac30102fee"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5
}
Fetched 2 record(s) in 1ms

```

## Listando todos os pokemons com altura menor ou igual que 0.5

```
amanda-Inspiron-7520(mongod-2.4.9) be-mean> var query = {height: {$lte:0.5}}

amanda-Inspiron-7520(mongod-2.4.9) be-mean> db.pokemons.find(query)
{
  "_id": ObjectId("5651f21e2b465aac30102fea"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "height": 0.4
}
{
  "_id": ObjectId("5651f3132b465aac30102feb"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
{
  "_id": ObjectId("5651f3912b465aac30102fee"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5
}
{
  "_id": ObjectId("5651f44e2b465aac30102fef"),
  "name": "Caterpie",
  "description": "Larva lutadora",
  "type": "inseto",
  "attack": 30,
  "height": 0.3,
  "defense": 35
}
Fetched 4 record(s) in 1ms

```

## Listando todos os pokemons com nome 'Pikachu' ou com attack menor ou igual que 0.5

```
amanda-Inspiron-7520(mongod-2.4.9) be-mean> var query = {$or: [{name: 'Pikachu'},{attack:{$lte:0.5}}]}

amanda-Inspiron-7520(mongod-2.4.9) be-mean> db.pokemons.find(query)
{
  "_id": ObjectId("5651f21e2b465aac30102fea"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "height": 0.4
}
Fetched 1 record(s) in 1ms

```

## Listando todos os pokemons attack maior ou igual que 48 e com height menor ou igual que 0.5

```
amanda-Inspiron-7520(mongod-2.4.9) be-mean> var query = {$and: [{attack: {$gte:48}},{height:{$lte:0.4}}]}

amanda-Inspiron-7520(mongod-2.4.9) be-mean> db.pokemons.find(query)
{
  "_id": ObjectId("5651f21e2b465aac30102fea"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "height": 0.4
}
{
  "_id": ObjectId("5651f3132b465aac30102feb"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
Fetched 2 record(s) in 1ms

```
