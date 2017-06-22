# MongoDB - Aula 03 - Exercício
autor: [Michel Ferreira Souza](https://github.com/souzacristsf)

## Listando todos os pokemons com altura menor que 0.5  

```
Souza(mongod-3.0.8) be-mean-instagram> var query = {height: {$lt:0.5}}
Souza(mongod-3.0.8) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("5674ac74d12632ef2d1a59d3"),
  "name": "Pikachu",
  "description": "Rato eletrico bem fofinho",
  "type": "electric",
  "attack": 100,
  "height": 0.4
}
{
  "_id": ObjectId("5674afcca2c7534bd63c5b3b"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
{
  "_id": ObjectId("56786db492d46b4f834736dd"),
  "name": "Caterpie",
  "description": "Larva lutadora",
  "type": "inseto",
  "attack": 30,
  "height": 0.3,
  "defense": 35
}
Fetched 3 record(s) in 2ms


```

## Listando todos os pokemons com altura maior ou igual que 0.5

```
Souza(mongod-3.0.8) be-mean-instagram> var query = {height: {$gte:0.5}}
Souza(mongod-3.0.8) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("5674afd6a2c7534bd63c5b3c"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6
}
{
  "_id": ObjectId("5674afdea2c7534bd63c5b3d"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5
}
Fetched 2 record(s) in 1ms


```
## Listando todos os pokemons com altura menor ou igual que 0.5 e do tipo grama

```
Souza(mongod-3.0.8) be-mean-instagram> var query = {$and: [{height: {$lte:0.5}}, {type: /grama/}]}
Souza(mongod-3.0.8) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("5674afcca2c7534bd63c5b3b"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
Fetched 1 record(s) in 3ms
```

## Listando todos os pokemons com altura menor ou igual que 0.5

```
Souza(mongod-3.0.8) be-mean-instagram> var query = {height: {$lte:0.5}}
Souza(mongod-3.0.8) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("5674ac74d12632ef2d1a59d3"),
  "name": "Pikachu",
  "description": "Rato eletrico bem fofinho",
  "type": "electric",
  "attack": 100,
  "height": 0.4
}
{
  "_id": ObjectId("5674afcca2c7534bd63c5b3b"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
{
  "_id": ObjectId("5674afdea2c7534bd63c5b3d"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5
}
{
  "_id": ObjectId("56786db492d46b4f834736dd"),
  "name": "Caterpie",
  "description": "Larva lutadora",
  "type": "inseto",
  "attack": 30,
  "height": 0.3,
  "defense": 35
}
Fetched 4 record(s) in 8ms


```

## Listando todos os pokemons com nome 'Pikachu' ou com attack menor ou igual que 0.5

```
Souza(mongod-3.0.8) be-mean-instagram> var query = {$or: [{name: /Pikachu/i}, {attack:{$lte:0.5 }}]}
Souza(mongod-3.0.8) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("5674ac74d12632ef2d1a59d3"),
  "name": "Pikachu",
  "description": "Rato eletrico bem fofinho",
  "type": "electric",
  "attack": 100,
  "height": 0.4
}
Fetched 1 record(s) in 1ms



```

## Listando todos os pokemons attack maior ou igual que 48 e com height menor ou igual que 0.5

```
Souza(mongod-3.0.8) be-mean-instagram> var query = {$and: [{attack: {$gte:48}}, {height:{$lte:0.4 }}]}
Souza(mongod-3.0.8) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("5674ac74d12632ef2d1a59d3"),
  "name": "Pikachu",
  "description": "Rato eletrico bem fofinho",
  "type": "electric",
  "attack": 100,
  "height": 0.4
}
{
  "_id": ObjectId("5674afcca2c7534bd63c5b3b"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
Fetched 2 record(s) in 2ms


```
