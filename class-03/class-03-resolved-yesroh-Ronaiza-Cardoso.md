# MongoDB - Aula 03 - Exercício
autor: Ronaiza Cardoso

## Pokemon List
``` JavaScript
Ronaiza_Card(C:\Program Files\MongoDB\Server\3.2\bin\mongod.exe-3.2.7) be-mean-pokemons> db.pokemons.find({})
{
  "_id": ObjectId("577ba38306c3c41e402f538c"),
  "name": "Charizar",
  "description": "Charizard flies around the sky in search of powerful opponents.",
  "type": "Fogo",
  "attack": 70,
  "height": 1.7
}
{
  "_id": ObjectId("577ba3d906c3c41e402f538d"),
  "name": "Mariza",
  "description": "Lacradora contenporanea.",
  "type": "Fogo",
  "attack": 100,
  "height": 1.7
}
{
  "_id": ObjectId("577ba42406c3c41e402f538e"),
  "name": "Silvio Santos",
  "description": "A reprentatividade da meritocracia que funciona tal qual a roleta russa",
  "type": "Aviões de Dinheiro",
  "attack": 300,
  "height": 2.8
}
{
  "_id": ObjectId("577ba4ce06c3c41e402f538f"),
  "name": "Dikklma",
  "description": "Presidenta que não teve jogo de cintura em relação a corja de bandidos que a cercavão, ensava poder vencer apenas com a honestidade",
  "type": "Politica",
  "attack": 76,
  "defense": 0,
  "height": 1.9
}
{
  "_id": ObjectId("577ba51f06c3c41e402f5390"),
  "name": "Bolsonaro",
  "description": "Deputado direitista",
  "type": "Metralhadora de merda",
  "attack": 180,
  "defense": 500,
  "height": 1.5
}
Fetched 5 record(s) in 78ms


## 1. Liste todos Pokemons com a altura menor que 0.5;
``` JavaScript

Ronaiza_Card(C:\Program Files\MongoDB\Server\3.2\bin\mongod.exe-3.2.7) be-mean-pokemons> db.pokemons.find(query)
Fetched 0 record

```
## 2. Liste todos Pokemons com a altura maior ou igual que 0.5;

```JavaScript


Ronaiza_Card(C:\Program Files\MongoDB\Server\3.2\bin\mongod.exe-3.2.7) be-mean-pokemons> var query = {height: {$gte: 0.5}}
Ronaiza_Card(C:\Program Files\MongoDB\Server\3.2\bin\mongod.exe-3.2.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("577ba38306c3c41e402f538c"),
  "name": "Charizar",
  "description": "Charizard flies around the sky in search of powerful opponents.",
  "type": "Fogo",
  "attack": 70,
  "height": 1.7
}
{
  "_id": ObjectId("577ba3d906c3c41e402f538d"),
  "name": "Mariza",
  "description": "Lacradora contenporanea.",
  "type": "Fogo",
  "attack": 100,
  "height": 1.7
}
{
  "_id": ObjectId("577ba42406c3c41e402f538e"),
  "name": "Silvio Santos",
  "description": "A reprentatividade da meritocracia que funciona tal qual a roleta russa",
  "type": "Aviões de Dinheiro",
  "attack": 300,
  "height": 2.8
}
{
  "_id": ObjectId("577ba4ce06c3c41e402f538f"),
  "name": "Dikklma",
  "description": "Presidenta que não teve jogo de cintura em relação a corja de bandidos que a cercavão, ensava poder vencer apenas com a honestidade",
  "type": "Politica",
  "attack": 76,
  "defense": 0,
  "height": 1.9
}
{
  "_id": ObjectId("577ba51f06c3c41e402f5390"),
  "name": "Bolsonaro",
  "description": "Deputado direitista",
  "type": "Metralhadora de merda",
  "attack": 180,
  "defense": 500,
  "height": 1.5
}
Fetched 5 record(s) in 47ms


```

## 3. Liste todos Pokemons com a altura menor ou igual que 0.5 E do tipo grama;

```JavaScript

Ronaiza_Card(C:\Program Files\MongoDB\Server\3.2\bin\mongod.exe-3.2.7) be-mean-pokemons> var query = {$and:[{height: {$lte: 0.5}}, {descpription: "grama"}]}

Ronaiza_Card(C:\Program Files\MongoDB\Server\3.2\bin\mongod.exe-3.2.7) be-mean-pokemons> db.pokemons.find(query)

Fetched 0 record(s) in 0ms

```

## 4. Liste todos Pokemons com o name `Pikachu` OU com attack menor ou igual que 0.5;

``` JavaScript

Ronaiza_Card(C:\Program Files\MongoDB\Server\3.2\bin\mongod.exe-3.2.7) be-mean-pokemons> var query = {$or:[{name: "Pikachu"}, {attack: {$lte: 0.5}}]}

Ronaiza_Card(C:\Program Files\MongoDB\Server\3.2\bin\mongod.exe-3.2.7) be-mean-pokemons> db.pokemons.find(query)

Fetched 0 record(s) in 25ms

```

## 5. Liste todos Pokemons com o attack MAIOR OU IGUAL QUE 48 E com  height menor ou igual que 0.5;

``` JavaScript

Ronaiza_Card(C:\Program Files\MongoDB\Server\3.2\bin\mongod.exe-3.2.7) be-mean-pokemons>  var query = {$and:[{attack:{$gte: 48}}, {height: {$lte: 0.5}}]}

Ronaiza_Card(C:\Program Files\MongoDB\Server\3.2\bin\mongod.exe-3.2.7) be-mean-pokemons> db.pokemons.find(query)

Fetched 0 record(s) in 1ms

```
