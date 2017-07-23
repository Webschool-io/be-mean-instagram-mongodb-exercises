# MongoDB - Aula 03 - Exercício
autor: Pablo R. Dinella

## 1. Liste todos Pokemons com a altura menor que 0.5;

```
Pablos-MacBook-Air(mongod-3.0.7) be-mean-pokemons> var query = {height:{$lt:0.5}}
Pablos-MacBook-Air(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5643a587c07db82a129bc6fb"),
  "name": "Weedle",
  "description": "Weedle has an extremely acute sense of smell",
  "attack": 35,
  "defense": 30,
  "height": 0.3
}
Fetched 1 record(s) in 13ms
```

## 2. Liste todos Pokemons com a altura maior ou igual que 0.5;

```
Pablos-MacBook-Air(mongod-3.0.7) be-mean-pokemons> var query = {height:{$gte:0.5}}
Pablos-MacBook-Air(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5643a1f8c07db82a129bc6f8"),
  "name": "rain-dish",
  "description": "Blastoise has water spouts that protrude from its shell",
  "attack": 82,
  "defense": 100,
  "height": 1.6
}
{
  "_id": ObjectId("5643a4dfc07db82a129bc6f9"),
  "name": "Butterfree",
  "description": "Butterfree is a Bug/Flying type Pokemon",
  "attack": 45,
  "defense": 50,
  "height": 1.09
}
{
  "_id": ObjectId("5643a54cc07db82a129bc6fa"),
  "name": "metapod",
  "description": "The shell covering this Pokémons body is as hard as an iron slab",
  "attack": 20,
  "defense": 55,
  "height": 0.71
}
{
  "_id": ObjectId("5643a5b1c07db82a129bc6fc"),
  "name": "Kakuna",
  "description": "Kakuna é legal",
  "attack": 25,
  "defense": 50,
  "height": 0.61
}
Fetched 4 record(s) in 5ms
```

## 3. Liste todos Pokemons com a altura menor ou igual que 0.5 E do tipo grama;

**PS: Como meus pokemons não tinham o campo tipo, fiz com defense e com height 1 pra retornar mais resultados pra ver se eu sei usar o $or... Foi mal**

```
Pablos-MacBook-Air(mongod-3.0.7) be-mean-pokemons> var query = {$or:[{defense:30},{height:{$lt:1}}]}
Pablos-MacBook-Air(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5643a54cc07db82a129bc6fa"),
  "name": "metapod",
  "description": "The shell covering this Pokémons body is as hard as an iron slab",
  "attack": 20,
  "defense": 55,
  "height": 0.71
}
{
  "_id": ObjectId("5643a587c07db82a129bc6fb"),
  "name": "Weedle",
  "description": "Weedle has an extremely acute sense of smell",
  "attack": 35,
  "defense": 30,
  "height": 0.3
}
{
  "_id": ObjectId("5643a5b1c07db82a129bc6fc"),
  "name": "Kakuna",
  "description": "Kakuna é legal",
  "attack": 25,
  "defense": 50,
  "height": 0.61
}
Fetched 3 record(s) in 9ms
```

## 4. Liste todos Pokemons com o name `Pikachu` OU com attack menor ou igual que 0.5;

```
Pablos-MacBook-Air(mongod-3.0.7) be-mean-pokemons> var query = {$or:[{name:"Pikachu"},{attack:{$lte:50}}]}
Pablos-MacBook-Air(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5643a4dfc07db82a129bc6f9"),
  "name": "Butterfree",
  "description": "Butterfree is a Bug/Flying type Pokemon",
  "attack": 45,
  "defense": 50,
  "height": 1.09
}
{
  "_id": ObjectId("5643a54cc07db82a129bc6fa"),
  "name": "metapod",
  "description": "The shell covering this Pokémons body is as hard as an iron slab",
  "attack": 20,
  "defense": 55,
  "height": 0.71
}
{
  "_id": ObjectId("5643a587c07db82a129bc6fb"),
  "name": "Weedle",
  "description": "Weedle has an extremely acute sense of smell",
  "attack": 35,
  "defense": 30,
  "height": 0.3
}
{
  "_id": ObjectId("5643a5b1c07db82a129bc6fc"),
  "name": "Kakuna",
  "description": "Kakuna é legal",
  "attack": 25,
  "defense": 50,
  "height": 0.61
}
Fetched 4 record(s) in 4ms
```

## 5. Liste todos Pokemons com o attack MAIOR OU IGUAL QUE 48 E com  height menor ou igual que 0.5;

```
Pablos-MacBook-Air(mongod-3.0.7) be-mean-pokemons> var query = {$and:[{attack:{$gte:48}},{height:{$lte:0.5}}]}
Pablos-MacBook-Air(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
Fetched 0 record(s) in 1ms
```
**Não tenho pokemons com essas características :/**
